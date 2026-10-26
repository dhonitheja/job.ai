# Tracker contract

CSV columns:
record_id,source,source_job_id,company,title,job_url,location,work_mode,seniority,status,saved_at,applied_at,updated_at,next_action,next_action_date,notes,status_evidence

Status enum: saved, preparing, applied, interviewing, offer, rejected, withdrawn, closed.
Use a stable record ID and ISO 8601 dates; null/blank means unknown. Record status changes with date, previous/new status, and user/evidence attribution in JSON history or CSV notes. An application date must not be invented. Updating a status must not erase prior history. Date-sensitive actions use the user's timezone when known. Suggested next actions are not scheduled reminders.

On import, validate columns and statuses, retain original data, surface malformed dates, and merge only matching stable IDs or verified canonical job URLs. Never merge merely because company and title match. Preserve custom columns in exports. Quote CSV fields correctly and neutralize cells starting with =, +, -, @, tab or carriage return to prevent spreadsheet formula execution. Use JSON when exact raw values must be preserved.

Default export includes minimal job and workflow data, not the full resume, protected traits, credentials, or unnecessary contact details. Users can request removal or correction. Do not promise deletion from ChatGPT account history. No server-side storage or cross-chat synchronization is implemented.

Example matching arithmetic for validation: category fractions 0.75, 0.5, 1, 0 with all categories active yield round(33.75+15+15+0)=64. With preferred criteria absent, active weight is 90 and score is round(100*63.75/90)=71.