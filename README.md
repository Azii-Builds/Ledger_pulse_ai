# LedgerPulse

**AI-powered document collection and reconciliation for small accounting firms.**

LedgerPulse takes the repetitive work out of monthly closing. It collects client documents, extracts data with OCR, syncs bank statements, and matches every transaction to its invoice, so CAs spend their time on advice instead of copying data between Tally, Excel, bank statements, and GST portals.

---

## The Problem

Small accounting firms lose hours every month to:

- **Manual data entry** across Tally, Excel, bank statements, and GST portals, which causes errors
- **Chasing clients** for missing bills, statements, and invoices
- **Month-end closing** checks across sales, purchases, expenses, payroll, and bank balances
- **Hidden mistakes**, such as duplicate bills, wrong entries, suspicious payments, and missing invoices
- **Audit prep**, where proof must be gathered for every important entry
- **Clients who can't read financial reports** and just want to know "Why is profit low?" or "Do I have enough cash?"
- **Juggling many clients**, each with different deadlines, files, and issues

## The Solution

LedgerPulse starts with the highest-impact workflow, **client document collection plus bank/invoice reconciliation**, and builds outward from there.

## Features

### Core (MVP)
- **Client document portal**: secure upload links per client, with automatic reminders for missing documents (WhatsApp/email)
- **OCR data extraction**: pulls vendor, invoice number, date, GSTIN, tax, and totals from PDFs, scans, and photos
- **Bank statement sync**: real-time feeds where supported, plus PDF/CSV/Excel statement import
- **Auto-reconciliation**: AI matches bank transactions to invoices and ledger entries, with confidence scores and a one-click review queue
- **Duplicate and anomaly detection**: flags duplicate bills, unusual amounts, missing invoices, and suspicious payments
- **Multi-client dashboard**: deadlines, pending documents, and reconciliation status for every client in one view

### Planned
- Tally export/import (XML) and Excel export
- GST return cross-checks (GSTR-2B vs purchase register)
- Month-end closing checklist with adjustment suggestions
- Audit pack generator that links each entry to its supporting evidence
- Plain-language "Ask your numbers" assistant for business owners
- Payroll and expense integrations
- Role-based access, approvals, and full audit trail

## How It Works

```
Client uploads docs  ->  OCR + AI extraction  ->  Bank sync / statement import
        |                                                    |
        +---------->  Auto-match and reconcile  <-----------+
                              |
              Review queue (exceptions only)
                              |
            Tally/Excel export  ·  Audit-ready pack
```

## Tech Stack

| Layer | Choice |
|-------|--------|
| Frontend | React, TypeScript, Tailwind CSS |
| Backend | Python, FastAPI |
| Database | PostgreSQL |
| Storage | S3-compatible object storage |
| OCR / extraction | Document OCR with LLM-based field extraction |
| Matching engine | Rule-based matching plus LLM for ambiguous cases |
| Bank data | Account Aggregator (India) / bank-feed provider, plus statement parsers |
| Queue | Redis and Celery |
| Auth | JWT with role-based access |

## Getting Started

```bash
# Clone
git clone https://github.com/<your-username>/ledgerpulse.git
cd ledgerpulse

# Backend
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env    # add your keys
uvicorn app.main:app --reload

# Frontend
cd ../frontend
npm install
npm run dev
```

## Configuration

Copy `.env.example` to `.env` and set:

```
DATABASE_URL=
STORAGE_BUCKET=
LLM_API_KEY=
OCR_PROVIDER=
BANK_FEED_PROVIDER=
JWT_SECRET=
```

## Security and Privacy

- Client financial data is encrypted in transit and at rest
- Data is isolated per firm and per client
- Every action is recorded in an audit log
- AI suggestions are always reviewable. LedgerPulse never posts entries without CA approval.

## Roadmap

- [ ] Client document portal and reminders
- [ ] OCR extraction pipeline
- [ ] Statement import (PDF/CSV/Excel)
- [ ] Reconciliation engine and review queue
- [ ] Live bank sync
- [ ] Duplicate and anomaly detection
- [ ] Tally integration
- [ ] GST cross-checks
- [ ] Audit pack generator
- [ ] Owner-facing Q&A assistant

## Contributing

Contributions are welcome. Please open an issue to discuss major changes before submitting a pull request.

## Disclaimer

LedgerPulse is an assistive tool. Outputs should be reviewed by a qualified professional before being used for filings or financial decisions.

## License

MIT
