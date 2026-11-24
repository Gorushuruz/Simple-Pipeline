# Simple-Pipeline

A single-file, drag-and-drop pipeline board for tracking leads, estimates, and jobs. There is no server, build step, or dependencies: open `Simple-Pipeline.html` in a browser and it works. All data is stored in the browser's `localStorage`.

## Quick start

1. Open `Simple-Pipeline.html` in a modern desktop browser (Chrome, Edge, Firefox, Safari).
2. The first load comes with 30 sample customers (10 leads, 10 estimates, 10 jobs).
3. Click **Add New** to create a record, or click any card to see its details.

## Features

### Board
- **Tabs** (Leads, Estimates, Jobs by default), each with its own set of stage columns.
- Every column shows a record count and the total dollar value of its cards.
- Move a card by dragging it to another column, or by using the status dropdown on the card.
- Drag a card onto a **tab** to move it to that tab. It lands in the tab's first stage.

### Customizing the board
| Action | How |
| --- | --- |
| Rename the app | Click the title ("Pipeline") in the top left and type. Enter saves, Escape cancels. |
| Add a tab | Click **+ Tab**. |
| Rename a tab | Double-click it. |
| Reorder tabs | Drag a tab onto another tab. |
| Delete a tab | Click the × on the tab (asks for confirmation; its records go to Trash). |
| Add a stage | Click **+ Add stage**. |
| Rename a stage | Click the stage title and type. Enter or clicking away saves. |
| Reorder stages | Drag a column header onto another column. |
| Delete a stage | Click the × in the column header (a board always keeps at least one stage). |

### Records
Each record holds: customer name, phone, email, address, service requested, value, status, assigned employee, a date, a lead source (leads) or record number (other tabs), internal notes, and image attachments.

- The date means "Date created" for leads, "Date sent" for estimates, and "Scheduled date" for jobs.
- Validation on save: name and service are required, phone needs at least 7 digits, value must be 0 or more.
- Click a card to open the details drawer, where you can **Edit** or **Delete** it.

### Search and filter
- Search by **All fields**, name, phone, service, or number/source.
- Click **Filter** to show or hide the employee filter. Hiding it clears the filter.

### Employees
Click **Employees** to open the manager.

- **Add** a custom employee by typing a name. Names are limited to 40 characters. Duplicates (case-insensitive) and the reserved name "Unassigned" are rejected.
- **Remove** an employee with the Remove button. The confirmation shows how many active records they own. Those records, including ones in Trash, become **Unassigned**.
- Employees appear in the record form and in the employee filter.

### Image attachments
In a record's details drawer, use **Add image** under Attachments.

- Select one or more image files, up to **8 per record**.
- Images are resized to at most 1200 px on the longest side and saved as JPEG (quality 0.8) so they fit in browser storage. Transparent areas become white.
- Click a thumbnail to view it larger. Click its × to remove it.
- Non-image files, unreadable images, and the 9th image are rejected with a message. If browser storage is full, the add is rolled back with an explanation.

### Trash
- Deleted records, stages, and tabs go to **Trash** rather than being erased.
- **Restore** puts a record back. If its tab was deleted, the tab is restored too. If its stage no longer exists, the stage is re-added.
- **Empty Trash** permanently deletes everything in it.

### Export and import
- **Export** shows a JSON text block. Select all, copy it, and save it somewhere safe.
- **Import** takes that text and **replaces** all current tabs, records, trash, employees, and the title (after a confirmation).
- Exports from older versions without an employee list still import. The employee list is rebuilt from the names on the records.
- Exports include attachments as embedded text, so they can get large when images are attached.
