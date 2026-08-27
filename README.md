# Abhyasikha School Supervision V5

## Key behavior
- The user-facing `index.html` must be hosted on HTTPS. Do not use the Apps Script `/exec` URL as the UI.
- Apps Script is the backend for Google Sheets and Drive.
- A live draft is NOT saved when the user merely fills the check-in form or refreshes before pressing **Check in now**.
- The session is created and persisted only after check-in is submitted.
- After check-in, refresh resumes the checkout page with the active session.
- A live session expires automatically after 3 hours without checkout; late checkout is rejected and the record is marked `EXPIRED`.
- Checkout has no back button.
- After successful checkout, local session storage is cleared and the feedback screen is shown. A new session is created only when the user starts a new check-in.
- Check-in time is the start of the Abhyasikha session. There is no separate Abhyasikha Program Time column.
- Google Sheet stores latitude, longitude, and clickable Google Maps links for check-in and checkout.
- `setup()` adds conditional formatting: incomplete/checked-in rows are highlighted; completed rows are green.

## Setup
1. Put your spreadsheet ID in `Code.gs`.
2. Run `setup()` once.
3. Deploy Apps Script as Web App: Execute as **Me**, Who has access **Anyone**.
4. Put the `/exec` URL in `index.html` as `API`.
5. Host `index.html` on an HTTPS site.
6. Redeploy the Apps Script whenever `Code.gs` changes.

## Sheet columns
Record ID, Visit Type, Supervisor Name, School Name, Visit Date, School Opening Time, School Closing Time, Check In Time, Check In Photo URL, Check In Latitude, Check In Longitude, Check In Location, Check In GPS Accuracy, Check Out Time, Check Out Photo URL, Check Out Latitude, Check Out Longitude, Check Out Location, Check Out GPS Accuracy, Duration HH:MM, Notes, Photo Submitted At, Status, Created At, Updated At, User Agent.

## Important migration note
`setup()` removes the old **Abhyasikha Program Time** column from the Visits sheet and replaces the header row with the V5 layout. Back up the sheet first if it contains production data you need to preserve.
