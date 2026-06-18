# Project Management Dashboard

Standalone JavaScript dashboard for combining worker Excel sheets into one project management view.

## Features

- Import `.xlsx`, `.xls`, `.xlsm`, or `.csv` files directly in the browser
- Combine separate worker sheets into one project table
- Track active jobs, week hours, overdue work, due-soon work, and open notes
- Filter by worker, client, due status, remarks, and search text
- View worker workload and weekly availability
- Adjust weekly worker capacity
- Import Microsoft Planner tasks from Microsoft Graph
- Export filtered rows to CSV
- Print the dashboard

## Use

Open `index.html` in a browser, then click **Import Excel** and choose your workbook.

The expected workbook layout is:

- One sheet per worker
- Header row containing `Job Number`, `Client`, `Project`, weekday hour columns, `Notes`, `Due`, and `Remarks`
- Worker name in the first row or as the sheet name

No server is required.

## Microsoft Planner Feed

Planner import runs in the browser through Microsoft Graph. Create a Microsoft Entra app registration and configure it as a single-page application.

Required setup:

- Redirect URI: `https://ioannisbekas.github.io/project-management-dashboard/`
- Platform type: Single-page application
- Delegated API permissions: `User.Read` and `Tasks.Read`

Then open the live dashboard, enter the Application client ID and tenant ID, connect to Planner, load plans, and import tasks.

Planner tasks do not include a standard hours field. The dashboard uses:

- hours written in the task title, such as `Shop drawings 5h`
- otherwise the dashboard's default Planner task hours value

If a Planner task is assigned to multiple people, the task hours are split across assignees.
