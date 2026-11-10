---
layout: default
title: "Type anything"
permalink: /write/
description: "A blank space. Type anything. It stays in your browser only."
---

<div id="type-box">
  <textarea id="type-text" rows="1" spellcheck="false"
            aria-label="Type anything" placeholder="type anything..."></textarea>
</div>

<div id="type-hint">
  <span>enter to save · shift+enter for new line</span>
  <span id="type-status" aria-live="polite"></span>
  <button id="type-clear" type="button">clear</button>
</div>

<style>
#type-box {
  position: relative;
  z-index: 1;
  height: 60vh;
  min-height: 260px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: text;
}

#type-text {
  display: block;
  width: 100%;
  max-height: 100%;
  margin: 0;
  padding: 0;
  border: none;
  outline: none;
  resize: none;
  overflow: hidden;
  background: transparent;
  text-align: center;
  font-family: var(--font-main);
  font-weight: 600;
  line-height: 1.25;
  color: var(--text-color);
  caret-color: var(--text-color);
  overflow-wrap: anywhere;
}

#type-text::placeholder {
  color: var(--text-color);
  opacity: 0.35;
}

#type-hint {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.8em;
  font-size: 0.6em;
  opacity: 0.6;
  margin-bottom: 1.5rem;
}

#type-clear {
  background: none;
  border: none;
  padding: 0;
  font: inherit;
  color: inherit;
  text-decoration: underline;
  cursor: pointer;
}
</style>

<script>
(function () {
  const KEY = 'racc-type-anything';
  const box = document.getElementById('type-box');
  const text = document.getElementById('type-text');
  const status = document.getElementById('type-status');
  const clearBtn = document.getElementById('type-clear');

  const MAX = 320;  /* px, biggest the text gets */
  const MIN = 12;  /* px, smallest before it starts scrolling */
  let statusTimeout;

  function load() {
    try { return localStorage.getItem(KEY) || ''; } catch (e) { return ''; }
  }

  function save(value) {
    try {
      if (value) localStorage.setItem(KEY, value);
      else localStorage.removeItem(KEY);
      return true;
    } catch (e) { return false; }
  }

  function flash(msg) {
    clearTimeout(statusTimeout);
    status.textContent = msg;
    statusTimeout = setTimeout(() => status.textContent = '', 1500);
  }

  function heightAt(size) {
    text.style.fontSize = size + 'px';
    text.style.height = 'auto';
    return text.scrollHeight;
  }

  /* biggest font size where all the text still fits in the box */
  function fit() {
    const room = box.clientHeight;
    text.style.maxHeight = 'none';
    let lo = MIN, hi = MAX;
    if (heightAt(MAX) <= room) lo = MAX;
    else {
      while (hi - lo > 0.5) {
        const mid = (lo + hi) / 2;
        if (heightAt(mid) <= room) lo = mid; else hi = mid;
      }
    }
    const h = heightAt(lo);
    text.style.maxHeight = '';
    text.style.height = Math.min(h, room) + 'px';
    text.style.overflowY = h > room ? 'auto' : 'hidden';
  }

  text.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' && !e.shiftKey && !e.isComposing) {
      e.preventDefault();
      flash(save(text.value) ? 'saved ✓' : "couldn't save");
    }
  });

  text.addEventListener('input', fit);
  window.addEventListener('resize', fit);
  box.addEventListener('click', (e) => { if (e.target === box) text.focus(); });

  clearBtn.addEventListener('click', () => {
    text.value = '';
    save('');
    fit();
    text.focus();
    flash('cleared');
  });

  text.value = load();
  fit();
  text.focus();
  text.setSelectionRange(text.value.length, text.value.length);
})();
</script>
