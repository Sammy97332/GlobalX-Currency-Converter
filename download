/**
 * GlobalX Currency Converter — Main Script
 * Author : Nkrumah Samuel Kojo
 * Course : PBSE304 · Pentecost University
 * Date   : November 2025
 *
 * Features:
 *  - Static exchange-rate conversion (Nov 2025 reference rates)
 *  - Conversion history with fade-in animation
 *  - Swap currencies
 *  - Clear history
 *  - Dark / light theme toggle (persisted in localStorage)
 */

'use strict';

/* ── Exchange Rates ─────────────────────────────────────────── */
/**
 * Static reference rates (Nov 2025).
 * Key  : base currency
 * Value: object mapping target currency → rate
 *
 * NOTE: For a production app, replace with a live API call
 * e.g. https://www.exchangerate-api.com or https://frankfurter.app
 */
const RATES = {
  USD: { GHS: 11.00, EUR: 0.93,  GBP: 0.79,  JPY: 151.00, CNY: 7.10  },
  GHS: { USD: 0.091, EUR: 0.062, GBP: 0.053,  JPY: 10.00,  CNY: 0.47  },
  EUR: { USD: 1.07,  GHS: 16.00, GBP: 0.85,   JPY: 160.00, CNY: 7.70  },
  GBP: { USD: 1.26,  GHS: 19.00, EUR: 1.17,   JPY: 185.00, CNY: 8.90  },
  JPY: { USD: 0.0066,GHS: 0.10,  EUR: 0.0063, GBP: 0.0054, CNY: 0.048 },
  CNY: { USD: 0.14,  GHS: 2.10,  EUR: 0.13,   GBP: 0.11,   JPY: 21.00 },
};

/* ── DOM References ─────────────────────────────────────────── */
const amountEl      = document.getElementById('amount');
const fromEl        = document.getElementById('from-currency');
const toEl          = document.getElementById('to-currency');
const resultTextEl  = document.getElementById('result-text');
const rateInfoEl    = document.getElementById('rate-info');
const timestampEl   = document.getElementById('timestamp');
const historyBody   = document.getElementById('history-body');
const historyCount  = document.getElementById('history-count');
const emptyRow      = document.getElementById('empty-row');
const themeToggle   = document.getElementById('theme-toggle');

/* ── State ──────────────────────────────────────────────────── */
let entryCount = 0;

/* ── Core: Convert ──────────────────────────────────────────── */
/**
 * Reads the form inputs, computes the conversion, updates the
 * result display, and appends a new row to the history table.
 */
function convert() {
  const amount = parseFloat(amountEl.value);
  const from   = fromEl.value;
  const to     = toEl.value;

  // --- Validation ---
  if (!amount || amount <= 0 || isNaN(amount)) {
    showResult('⚠ Please enter a valid positive amount.', '', '');
    return;
  }

  if (from === to) {
    showResult(
      `${formatNumber(amount)} ${from} = ${formatNumber(amount)} ${to}`,
      'Same currency — no conversion needed.',
      new Date().toLocaleString()
    );
    return;
  }

  // --- Compute ---
  const rate   = RATES[from][to];
  const result = amount * rate;
  const now    = new Date();

  // --- Display result ---
  showResult(
    `${formatNumber(amount)} ${from} = ${formatNumber(result)} ${to}`,
    `Rate: 1 ${from} = ${rate} ${to}`,
    now.toLocaleString(),
    true
  );

  // --- Append history row ---
  appendHistory(amount, from, to, result, rate, now);
}

/* ── UI Helpers ─────────────────────────────────────────────── */

/**
 * Updates the result display area.
 * @param {string} mainText   - Primary conversion result text
 * @param {string} rateText   - Rate info (secondary line)
 * @param {string} timeText   - Timestamp string
 * @param {boolean} success   - If true, applies a success highlight style
 */
function showResult(mainText, rateText, timeText, success = false) {
  resultTextEl.textContent = mainText;
  resultTextEl.classList.toggle('has-result', success);
  rateInfoEl.textContent   = rateText;
  timestampEl.textContent  = timeText;
}

/**
 * Formats a number to a human-readable string (max 4 decimal places,
 * trailing zeros stripped).
 * @param {number} num
 * @returns {string}
 */
function formatNumber(num) {
  return parseFloat(num.toFixed(4)).toLocaleString(undefined, {
    minimumFractionDigits: 2,
    maximumFractionDigits: 4,
  });
}

/**
 * Appends a conversion record to the history table.
 */
function appendHistory(amount, from, to, result, rate, date) {
  // Remove the "empty" placeholder row on first entry
  if (emptyRow) emptyRow.remove();

  entryCount++;
  updateHistoryCount();

  const row = document.createElement('tr');
  row.classList.add('fade-in');
  row.innerHTML = `
    <td>${formatNumber(amount)}</td>
    <td>${from}</td>
    <td>${to}</td>
    <td><strong>${formatNumber(result)}</strong></td>
    <td>${rate}</td>
    <td>${date.toLocaleString()}</td>
  `;
  historyBody.prepend(row);
}

/**
 * Updates the history counter badge.
 */
function updateHistoryCount() {
  historyCount.textContent = `${entryCount} entr${entryCount === 1 ? 'y' : 'ies'}`;
}

/* ── Theme Toggle ───────────────────────────────────────────── */

/** Applies the saved theme preference on page load. */
function initTheme() {
  const saved = localStorage.getItem('globalx-theme');
  if (saved === 'light') {
    document.body.classList.add('light');
    themeToggle.textContent = '☀️';
  }
}

/** Toggles between dark and light modes and persists the choice. */
function toggleTheme() {
  const isLight = document.body.classList.toggle('light');
  themeToggle.textContent = isLight ? '☀️' : '🌙';
  localStorage.setItem('globalx-theme', isLight ? 'light' : 'dark');
}

/* ── Event Listeners ────────────────────────────────────────── */

// Convert button
document.getElementById('convert').addEventListener('click', convert);

// Allow Enter key to trigger conversion from the amount field
amountEl.addEventListener('keydown', (e) => {
  if (e.key === 'Enter') convert();
});

// Swap currencies
document.getElementById('swap').addEventListener('click', () => {
  const temp   = fromEl.value;
  fromEl.value = toEl.value;
  toEl.value   = temp;
});

// Clear history
document.getElementById('clear-history').addEventListener('click', () => {
  historyBody.innerHTML = '';
  entryCount = 0;
  updateHistoryCount();

  // Re-insert the empty placeholder
  const placeholder = document.createElement('tr');
  placeholder.id = 'empty-row';
  placeholder.innerHTML = `
    <td colspan="6" class="empty-msg">No conversions yet. Try converting something above!</td>
  `;
  historyBody.appendChild(placeholder);
});

// Theme toggle
themeToggle.addEventListener('click', toggleTheme);

/* ── Initialise ─────────────────────────────────────────────── */
initTheme();
