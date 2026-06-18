# Project Management Dashboard

Standalone JavaScript dashboard for combining worker Excel sheets into one project management view.

## Features

- Import `.xlsx`, `.xls`, `.xlsm`, or `.csv` files directly in the browser
- Combine separate worker sheets into one project table
- Track active jobs, week hours, overdue work, due-soon work, and open notes
- Filter by worker, client, due status, remarks, and search text
- View worker workload and weekly availability
- Adjust weekly worker capacity
- Export filtered rows to CSV
- Print the dashboard

## Use

Open `index.html` in a browser, then click **Import Excel** and choose your workbook.

The expected workbook layout is:

- One sheet per worker
- Header row containing `Job Number`, `Client`, `Project`, weekday hour columns, `Notes`, `Due`, and `Remarks`
- Worker name in the first row or as the sheet name

No server is required.
