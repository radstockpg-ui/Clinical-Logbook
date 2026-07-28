import React, { useState, useEffect, useMemo } from 'react';

const CATEGORIES = [
  'Respiratory',
  'Cardiovascular',
  'Sepsis / Infectious Disease',
  'Renal / Metabolic',
  'Neuro / Sedation',
  'GI / Nutrition',
  'Procedures',
  'Pharmacology',
  'Communication / Ethics',
  'Other'
];

const INDEPENDENCE_LEVELS = ['Observed', 'Assisted', 'Performed independently'];

const CATEGORY_STYLES = {
  'Respiratory': { bg: '#E3F2F1', text: '#0C5C5C' },
  'Cardiovascular': { bg: '#FBEAEA', text: '#9B3B3B' },
  'Sepsis / Infectious Disease': { bg: '#FBF1DE', text: '#A9720C' },
  'Renal / Metabolic': { bg: '#EAF3EA', text: '#3F7A47' },
  'Neuro / Sedation': { bg: '#EFE9F7', text: '#6247AA' },
  'GI / Nutrition': { bg: '#FBEEE3', text: '#B15C24' },
  'Procedures': { bg: '#FDEDED', text: '#B23A3A' },
  'Pharmacology': { bg: '#E9EDF9', text: '#3B4E9B' },
  'Communication / Ethics': { bg: '#E3F0F0', text: '#1F6E6E' },
  'Other': { bg: '#F0F0EE', text: '#6B7C7E' }
};

const COLORS = {
  petrol: '#0C5C5C',
  petrolSoft: '#E4F0EF',
  amber: '#A9720C',
  amberSoft: '#FBF1DE',
  amberBorder: '#E8D2A0',
  amberText: '#6B4A0C',
  border: '#DCE3E2',
  danger: '#B23A3A',
  dangerSoft: '#FDEDED'
};

const STORAGE_KEY = 'clinical-logbook-entries';

const emptyForm = {
  date: todayStr(),
  title: '',
  category: CATEGORIES[0],
  tags: '',
  whatIDid: '',
  whatILearnt: '',
  theoryToRevisit: '',
  independenceLevel: INDEPENDENCE_LEVELS[1]
};

function todayStr() {
  const d = new Date();
  const offset = d.getTimezoneOffset();
  const local = new Date(d.getTime() - offset * 60000);
  return local.toISOString().split('T')[0];
}

function formatDate(dateStr) {
  if (!dateStr) return '';
  const parts = dateStr.split('-');
  if (parts.length !== 3) return dateStr;
  const [y, m, d] = parts.map(Number);
  if (!y || !m || !d) return dateStr;
  const date = new Date(y, m - 1, d);
  return date.toLocaleDateString('en-US', { day: 'numeric', month: 'short', year: 'numeric' });
}

function generateId() {
  if (typeof crypto !== 'undefined' && crypto.randomUUID) {
    return crypto.randomUUID();
  }
  return Date.now().toString(36) + Math.random().toString(36).slice(2, 11);
}

function daysSpanned(entries) {
  if (entries.length === 0) return 0;
  const dates = entries.map(e => e.date).filter(Boolean).sort();
  if (dates.length === 0) return 0;
  const first = new Date(dates[0]);
  const last = new Date(dates[dates.length - 1]);
  const diff = Math.round((last - first) / (1000 * 60 * 60 * 24)) + 1;
  return diff > 0 ? diff : 1;
}

function IndependenceDots({ level }) {
  const idx = INDEPENDENCE_LEVELS.indexOf(level);
  const filled = idx === -1 ? 0 : idx + 1;
  const dots = INDEPENDENCE_LEVELS.map((_, i) => (i < filled ? '●' : '○')).join('');
  return (
    <span className="font-mono text-xs" style={{ color: COLORS.petrol }}>{dots}</span>
  );
}

function EntryCard({ entry, onEdit, onDelete, confirmDeleteId, setConfirmDeleteId }) {
  const style = CATEGORY_STYLES[entry.category] || CATEGORY_STYLES['Other'];
  return (
    <div className="bg-white rounded-xl border p-4" style={{ borderColor: COLORS.border }}>
      <div className="flex items-start justify-between gap-2 mb-2">
        <div className="min-w-0">
          <p className="text-sm font-semibold text-slate-800 truncate">
            {entry.title || 'Untitled entry'}
          </p>
          <div className="flex items-center gap-2 mt-0.5">
            <span className="font-mono text-xs text-slate-400">{formatDate(entry.date)}</span>
            <IndependenceDots level={entry.independenceLevel} />
          </div>
        </div>
        <span
          className="text-xs px-2 py-0.5 rounded-full font-medium shrink-0"
          style={{ backgroundColor: style.bg, color: style.text }}
        >
          {entry.category}
        </span>
      </div>

      {entry.whatIDid && (
        <div className="mb-2">
          <p className="text-xs font-mono uppercase tracking-wide text-slate-400 mb-0.5">What I did</p>
          <p className="text-sm text-slate-700 whitespace-pre-wrap">{entry.whatIDid}</p>
        </div>
      )}

      {entry.whatILearnt && (
        <div className="mb-2">
          <p className="text-xs font-mono uppercase tracking-wide text-slate-400 mb-0.5">What I learnt</p>
          <p className="text-sm text-slate-700 whitespace-pre-wrap">{entry.whatILearnt}</p>
        </div>
      )}

      {entry.theoryToRevisit && (
        <div className="rounded-lg p-2.5 mb-2" style={{ backgroundColor: COLORS.amberSoft }}>
          <p className="text-xs font-mono uppercase tracking-wide mb-0.5" style={{ color: COLORS.amber }}>
            Theory to revisit
          </p>
          <p className="text-sm whitespace-pre-wrap" style={{ color: COLORS.amberText }}>{entry.theoryToRevisit}</p>
        </div>
      )}

      {entry.tags && (
        <p className="text-xs text-slate-400 mb-1">Tags: {entry.tags}</p>
      )}

      <div className="flex items-center gap-4 pt-2 mt-1 border-t text-xs" style={{ borderColor: COLORS.border }}>
        <button onClick={() => onEdit(entry)} className="font-medium py-2" style={{ color: COLORS.petrol }}>
          Edit
        </button>
        {confirmDeleteId === entry.id ? (
          <>
            <span className="text-slate-400">Delete this entry?</span>
            <button onClick={() => onDelete(entry.id)} className="font-medium py-2" style={{ color: COLORS.danger }}>
              Yes, delete
            </button>
            <button onClick={() => setConfirmDeleteId(null)} className="text-slate-400 py-2">Cancel</button>
          </>
        ) : (
          <button onClick={() => setConfirmDeleteId(entry.id)} className="py-2" style={{ color: COLORS.danger }}>
            Delete
          </button>
        )}
      </div>
    </div>
  );
}

export default function ClinicalLogbook() {
  const [entries, setEntries] = useState([]);
  const [loading, setLoading] = useState(true);
  const [saving, setSaving] = useState(false);
  const [error, setError] = useState('');
  const [activeTab, setActiveTab] = useState('add');
  const [form, setForm] = useState(emptyForm);
  const [editingId, setEditingId] = useState(null);
  const [searchText, setSearchText] = useState('');
  const [categoryFilter, setCategoryFilter] = useState('All');
  const [sortOrder, setSortOrder] = useState('newest');
  const [confirmDeleteId, setConfirmDeleteId] = useState(null);
  const [visibleCount, setVisibleCount] = useState(30);
  const [formError, setFormError] = useState('');
  const [saveConfirmation, setSaveConfirmation] = useState('');

  useEffect(() => {
    let mounted = true;
    async function loadEntries() {
      try {
        const result = await window.storage.get(STORAGE_KEY, false);
        if (mounted && result && result.value) {
          const parsed = JSON.parse(result.value);
          if (Array.isArray(parsed)) {
            setEntries(parsed);
          }
        }
      } catch (e) {
        // Key doesn't exist yet on first use - start with an empty logbook.
      } finally {
        if (mounted) setLoading(false);
      }
    }
    loadEntries();
    return () => { mounted = false; };
  }, []);

  useEffect(() => {
    setVisibleCount(30);
  }, [searchText, categoryFilter, sortOrder]);

  async function persistEntries(updated) {
    setSaving(true);
    setError('');
    try {
      const result = await window.storage.set(STORAGE_KEY, JSON.stringify(updated), false);
      if (!result) {
        setError('Could not save that. Please try again.');
        return false;
      }
      return true;
    } catch (e) {
      setError('Could not save that. Please try again.');
      return false;
    } finally {
      setSaving(false);
    }
  }

  function updateForm(field, value) {
    setForm(prev => ({ ...prev, [field]: value }));
    if (formError) setFormError('');
  }

  function resetForm() {
    setForm(emptyForm);
    setEditingId(null);
    setFormError('');
  }

  async function handleSubmit(e) {
    e.preventDefault();
    if (!form.date) {
      setFormError('Add a date for this entry.');
      return;
    }
    if (!form.whatIDid.trim() && !form.whatILearnt.trim()) {
      setFormError('Add at least what you did or what you learnt.');
      return;
    }

    let updated;
    if (editingId) {
      updated = entries.map(en => (en.id === editingId ? { ...en, ...form, id: editingId } : en));
    } else {
      const newEntry = { ...form, id: generateId(), createdAt: new Date().toISOString() };
      updated = [...entries, newEntry];
    }

    const ok = await persistEntries(updated);
    if (ok) {
      setEntries(updated);
      setSaveConfirmation(editingId ? 'Entry updated.' : 'Entry saved.');
      setTimeout(() => setSaveConfirmation(''), 2000);
      const wasEditing = Boolean(editingId);
      resetForm();
      if (wasEditing) setActiveTab('view');
    }
  }

  function handleEdit(entry) {
    setForm({
      date: entry.date || todayStr(),
      title: entry.title || '',
      category: entry.category || CATEGORIES[0],
      tags: entry.tags || '',
      whatIDid: entry.whatIDid || '',
      whatILearnt: entry.whatILearnt || '',
      theoryToRevisit: entry.theoryToRevisit || '',
      independenceLevel: entry.independenceLevel || INDEPENDENCE_LEVELS[1]
    });
    setEditingId(entry.id);
    setFormError('');
    setActiveTab('add');
  }

  async function handleDelete(id) {
    const updated = entries.filter(en => en.id !== id);
    const ok = await persistEntries(updated);
    if (ok) setEntries(updated);
    setConfirmDeleteId(null);
  }

  function handleExport() {
    const sorted = [...entries].sort((a, b) => a.date.localeCompare(b.date));
    let text = 'CLINICAL LOGBOOK\n';
    text += `Exported: ${new Date().toLocaleDateString()}\n`;
    text += `Total entries: ${sorted.length}\n`;
    text += '='.repeat(50) + '\n\n';
    sorted.forEach(en => {
      text += `${formatDate(en.date)} — ${en.title || 'Untitled entry'}\n`;
      text += `Category: ${en.category}${en.independenceLevel ? '  |  Level: ' + en.independenceLevel : ''}\n`;
      if (en.tags) text += `Tags: ${en.tags}\n`;
      text += `\nWhat I did:\n${en.whatIDid || '-'}\n`;
      text += `\nWhat I learnt:\n${en.whatILearnt || '-'}\n`;
      if (en.theoryToRevisit) text += `\nTheory to revisit:\n${en.theoryToRevisit}\n`;
      text += '\n' + '-'.repeat(50) + '\n\n';
    });

    try {
      const blob = new Blob([text], { type: 'text/plain' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `clinical-logbook-${todayStr()}.txt`;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    } catch (e) {
      setError('Export failed. Please try again.');
    }
  }

  const filteredEntries = useMemo(() => {
    let result = entries;
    if (categoryFilter !== 'All') {
      result = result.filter(en => en.category === categoryFilter);
    }
    if (searchText.trim()) {
      const q = searchText.toLowerCase();
      result = result.filter(en =>
        (en.title || '').toLowerCase().includes(q) ||
        (en.whatIDid || '').toLowerCase().includes(q) ||
        (en.whatILearnt || '').toLowerCase().includes(q) ||
        (en.theoryToRevisit || '').toLowerCase().includes(q) ||
        (en.tags || '').toLowerCase().includes(q) ||
        (en.category || '').toLowerCase().includes(q)
      );
    }
    const sorted = [...result].sort((a, b) => {
      const cmp = (a.date || '').localeCompare(b.date || '') || (a.createdAt || '').localeCompare(b.createdAt || '');
      return sortOrder === 'newest' ? -cmp : cmp;
    });
    return sorted;
  }, [entries, categoryFilter, searchText, sortOrder]);

  return (
    <div className="min-h-screen bg-slate-50 pb-10">
      <div className="max-w-2xl mx-auto px-4 pt-6">
        <div className="mb-5">
          <span className="font-mono text-xs tracking-widest uppercase text-slate-400">
            Daily tracker
          </span>
          <h1 className="text-2xl font-bold tracking-tight text-slate-800">Clinical Logbook</h1>
        </div>

        {!loading && entries.length > 0 && (
          <div className="mb-4 px-0.5">
            <span className="text-xs text-slate-500">
              <span className="font-mono font-semibold text-slate-800">{entries.length}</span> entries logged over{' '}
              <span className="font-mono font-semibold text-slate-800">{daysSpanned(entries)}</span> days
            </span>
          </div>
        )}

        <div className="flex gap-1 p-1 rounded-lg mb-4" style={{ backgroundColor: COLORS.petrolSoft }}>
          <button
            onClick={() => setActiveTab('add')}
            className="flex-1 py-3 rounded-md text-sm font-medium transition-colors"
            style={activeTab === 'add'
              ? { backgroundColor: '#FFFFFF', color: COLORS.petrol, boxShadow: '0 1px 2px rgba(0,0,0,0.08)' }
              : { color: '#4B6664' }}
          >
            {editingId ? 'Edit entry' : 'New entry'}
          </button>
          <button
            onClick={() => setActiveTab('view')}
            className="flex-1 py-3 rounded-md text-sm font-medium transition-colors"
            style={activeTab === 'view'
              ? { backgroundColor: '#FFFFFF', color: COLORS.petrol, boxShadow: '0 1px 2px rgba(0,0,0,0.08)' }
              : { color: '#4B6664' }}
          >
            Logbook ({entries.length})
          </button>
        </div>

        {error && (
          <div className="mb-3 text-sm rounded-lg px-3 py-2" style={{ backgroundColor: COLORS.dangerSoft, color: COLORS.danger }}>
            {error}
          </div>
        )}
        {saveConfirmation && (
          <div className="mb-3 text-sm rounded-lg px-3 py-2" style={{ backgroundColor: COLORS.petrolSoft, color: COLORS.petrol }}>
            {saveConfirmation}
          </div>
        )}

        {loading ? (
          <div className="text-center py-16 text-sm text-slate-400">Loading your logbook…</div>
        ) : activeTab === 'add' ? (
          <form onSubmit={handleSubmit} className="bg-white rounded-xl border p-4 space-y-4" style={{ borderColor: COLORS.border }}>
            {editingId && (
              <div className="flex items-center justify-between text-sm px-3 py-2 rounded-lg" style={{ backgroundColor: COLORS.amberSoft, color: COLORS.amberText }}>
                <span>Editing entry from {formatDate(form.date)}</span>
                <button type="button" onClick={resetForm} className="underline">Cancel</button>
              </div>
            )}

            <p className="text-xs italic text-slate-400">
              Tip: describe cases by presentation, not by patient name or ID.
            </p>

            <div className="grid grid-cols-2 gap-3">
              <div>
                <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Date</label>
                <input
                  type="date"
                  value={form.date}
                  onChange={e => updateForm('date', e.target.value)}
                  className="w-full border rounded-lg px-3 py-2"
                  style={{ borderColor: COLORS.border, fontSize: '16px' }}
                />
              </div>
              <div>
                <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Category</label>
                <select
                  value={form.category}
                  onChange={e => updateForm('category', e.target.value)}
                  className="w-full border rounded-lg px-3 py-2"
                  style={{ borderColor: COLORS.border, fontSize: '16px' }}
                >
                  {CATEGORIES.map(c => <option key={c} value={c}>{c}</option>)}
                </select>
              </div>
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Case summary (optional)</label>
              <input
                type="text"
                value={form.title}
                onChange={e => updateForm('title', e.target.value)}
                placeholder="e.g. 58F septic shock 2° UTI"
                className="w-full border rounded-lg px-3 py-2"
                style={{ borderColor: COLORS.border, fontSize: '16px' }}
              />
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Independence level</label>
              <div className="flex gap-2">
                {INDEPENDENCE_LEVELS.map((level, i) => {
                  const isActive = form.independenceLevel === level;
                  return (
                    <button
                      type="button"
                      key={level}
                      onClick={() => updateForm('independenceLevel', level)}
                      className="flex-1 rounded-lg border py-2 px-1 text-center"
                      style={{
                        borderColor: isActive ? COLORS.petrol : COLORS.border,
                        backgroundColor: isActive ? COLORS.petrolSoft : '#FFFFFF'
                      }}
                    >
                      <div className="font-mono text-sm" style={{ color: COLORS.petrol }}>
                        {'●'.repeat(i + 1)}{'○'.repeat(2 - i)}
                      </div>
                      <div className="text-xs mt-0.5" style={{ color: isActive ? '#1E2B2E' : '#8A9A9C' }}>
                        {level}
                      </div>
                    </button>
                  );
                })}
              </div>
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">What I did</label>
              <textarea
                value={form.whatIDid}
                onChange={e => updateForm('whatIDid', e.target.value)}
                rows={3}
                placeholder="e.g. Assisted with intubation for hypoxic respiratory failure; titrated noradrenaline for septic shock"
                className="w-full border rounded-lg px-3 py-2"
                style={{ borderColor: COLORS.border, fontSize: '16px' }}
              />
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">What I learnt</label>
              <textarea
                value={form.whatILearnt}
                onChange={e => updateForm('whatILearnt', e.target.value)}
                rows={3}
                placeholder="e.g. Indications for early intubation; RSI drug doses"
                className="w-full border rounded-lg px-3 py-2"
                style={{ borderColor: COLORS.border, fontSize: '16px' }}
              />
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Theory to revisit</label>
              <textarea
                value={form.theoryToRevisit}
                onChange={e => updateForm('theoryToRevisit', e.target.value)}
                rows={2}
                placeholder="e.g. Surviving Sepsis Campaign guidelines, ARDSnet protocol"
                className="w-full border rounded-lg px-3 py-2"
                style={{ backgroundColor: COLORS.amberSoft, borderColor: COLORS.amberBorder, fontSize: '16px' }}
              />
            </div>

            <div>
              <label className="block text-xs font-mono uppercase tracking-wide text-slate-400 mb-1">Tags (optional, comma-separated)</label>
              <input
                type="text"
                value={form.tags}
                onChange={e => updateForm('tags', e.target.value)}
                placeholder="e.g. ARDS, vasopressors, ultrasound"
                className="w-full border rounded-lg px-3 py-2"
                style={{ borderColor: COLORS.border, fontSize: '16px' }}
              />
            </div>

            {formError && <p className="text-sm" style={{ color: COLORS.danger }}>{formError}</p>}

            <button
              type="submit"
              disabled={saving}
              className="w-full text-white font-medium py-2.5 rounded-lg disabled:opacity-50"
              style={{ backgroundColor: COLORS.petrol }}
            >
              {saving ? 'Saving…' : editingId ? 'Update entry' : 'Save entry'}
            </button>
          </form>
        ) : (
          <div>
            <div className="bg-white rounded-xl border p-3 mb-3 space-y-2" style={{ borderColor: COLORS.border }}>
              <input
                type="text"
                value={searchText}
                onChange={e => setSearchText(e.target.value)}
                placeholder="Search everything…"
                className="w-full border rounded-lg px-3 py-2"
                style={{ borderColor: COLORS.border, fontSize: '16px' }}
              />
              <div className="flex gap-2">
                <select
                  value={categoryFilter}
                  onChange={e => setCategoryFilter(e.target.value)}
                  className="flex-1 border rounded-lg px-2 py-1.5"
                  style={{ borderColor: COLORS.border, fontSize: '16px' }}
                >
                  <option value="All">All categories</option>
                  {CATEGORIES.map(c => <option key={c} value={c}>{c}</option>)}
                </select>
                <button
                  onClick={() => setSortOrder(s => (s === 'newest' ? 'oldest' : 'newest'))}
                  className="text-xs border rounded-lg px-3 py-1.5 text-slate-600 whitespace-nowrap"
                  style={{ borderColor: COLORS.border }}
                >
                  {sortOrder === 'newest' ? '↓ Newest first' : '↑ Oldest first'}
                </button>
              </div>
            </div>

            {entries.length > 0 && (
              <button onClick={handleExport} className="text-xs underline mb-3" style={{ color: COLORS.petrol }}>
                Export full logbook (.txt)
              </button>
            )}

            {filteredEntries.length === 0 ? (
              <div className="text-center py-14 text-sm text-slate-400">
                {entries.length === 0
                  ? 'No entries yet. Add your first one from the New entry tab.'
                  : 'No entries match your search.'}
              </div>
            ) : (
              <div className="space-y-3">
                {filteredEntries.slice(0, visibleCount).map(entry => (
                  <EntryCard
                    key={entry.id}
                    entry={entry}
                    onEdit={handleEdit}
                    onDelete={handleDelete}
                    confirmDeleteId={confirmDeleteId}
                    setConfirmDeleteId={setConfirmDeleteId}
                  />
                ))}
                {filteredEntries.length > visibleCount && (
                  <button
                    onClick={() => setVisibleCount(v => v + 30)}
                    className="w-full text-sm py-2"
                    style={{ color: COLORS.petrol }}
                  >
                    Show more ({filteredEntries.length - visibleCount} remaining)
                  </button>
                )}
              </div>
            )}

            <p className="text-xs text-slate-400 text-center mt-6">
              Entries save automatically and stay here across visits. Export a backup from time to time.
            </p>
          </div>
        )}
      </div>
    </div>
  );
}
