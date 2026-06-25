# Project Management Dashboard

Standalone JavaScript dashboard for combining worker Excel sheets into one project management view.

## Features

- Import `.xlsx`, `.xls`, `.xlsm`, or `.csv` files directly in the browser
- Combine separate worker sheets into one project table
- Track active jobs, week hours, overdue work, due-soon work, and open notes
- Filter by worker, client, due status, remarks, and search text
- View worker workload and weekly availability
- Adjust weekly worker capacity
- Import one Planner plan or all matching Planner plans from Microsoft Graph
- Add, edit, and delete project rows directly in the dashboard
- Export filtered rows to CSV
- Print the dashboard

## Use

Open `index.html` in a browser, then click **Import Excel** and choose your workbook.

The expected workbook layout is:

- One sheet per worker
- Header row containing `Job Number`, `Client`, `Project`, weekday hour columns, `Notes`, `Due`, and `Remarks`
- Worker name in the first row or as the sheet name

No server is required.

## Table Editing

Use the **Projects** table to edit the same fields that appear in the worker spreadsheets: worker, job number, client, project, weekday hours, notes, due date, and remarks. Click a cell, type the change, then press Enter or click away.

Use **New Row** to add a browser-saved row. Imported Excel or Planner rows edited in the table are saved as browser-local overrides, included in dashboard totals, and exported with CSV. They are not shared with other users and do not write back into Excel or Planner.

## Microsoft Planner Feed

Planner import runs in the browser through Microsoft Graph. Create a Microsoft Entra app registration and configure it as a single-page application.

Required setup:

- Redirect URI: `https://ioannisbekas.github.io/project-management-dashboard/`
- Platform type: Single-page application
- Delegated API permissions: `User.Read` and `Tasks.Read`

Then open the live dashboard, enter the Application client ID and tenant ID, connect to Planner, and load plans.

Use **Import Selected Plan** for one plan. Use **Import Matching Plans** to pull many job plans at once. The include/exclude filters match plan names, separated by commas. For example:

- Include: `26-, 25-`
- Exclude: `template, archive`

The dashboard shows a Planner Sync summary with each imported plan, open tasks, generated dashboard rows, and booked hours.

Planner tasks do not include a standard hours field. The dashboard uses:

- hours written in the task title, such as `Shop drawings 5h`
- otherwise the dashboard's default Planner task hours value

If a Planner task is assigned to multiple people, the task hours are split across assignees.

For plan names like `26-051 U of M Battery Plant Addition - D&H Fire`, the dashboard maps:

- `26-051` to Job
- `D&H Fire` to Client
- the Planner task title to Project
