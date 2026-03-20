# Team Manager SaaS

A fully functional, single-file team and project management web application with SaaS-style design.

![Team Manager SaaS](./screenshot.png)

## Features

- **Dashboard** — Summary cards with key metrics, recent activity feed, and project progress bars
- **Projects** — Grid view of all projects with status badges, member avatars, and progress tracking
- **Kanban Board** — Drag-and-drop task management across 4 columns (To Do, In Progress, In Review, Done)
- **Tasks** — Full task list with filtering, sorting, and inline status toggles
- **Team** — Team member cards with workload overview and task assignments
- **Analytics** — Interactive charts (bar, pie, horizontal bar) built with HTML5 Canvas
- **Global Search** — Real-time search across tasks, projects, and team members
- **Responsive Design** — Collapsible sidebar for mobile devices
- **Dark Theme** — Modern dark UI with CSS variables for easy theming
- **Local Storage** — All data persists in browser localStorage

## Tech Stack

- **HTML5** — Semantic structure and markup
- **CSS3** — Styling, animations, CSS variables for theming, flexbox/grid layouts
- **Vanilla JavaScript (ES6+)** — All application logic, state management, routing
- **localStorage** — Client-side data persistence (no server required)
- **HTML5 Canvas** — Custom chart rendering (no external libraries)
- **HTML5 Drag & Drop API** — Native drag-and-drop for Kanban board

## How to Run

1. Download or clone this repository
2. Open `index.html` in any modern web browser (Chrome, Firefox, Edge, Safari)
3. That's it! The app will automatically load with demo data on first launch

No build tools, no dependencies, no server required.

## Data Storage

All application data is stored in the browser's **localStorage** under the key `teamManagerState`. This includes:

- **Projects** — Name, description, status, due date, assigned members
- **Tasks** — Title, description, project, assignee, status, priority, due date
- **Team Members** — Name, role, email, avatar color
- **Activity Log** — Timestamped history of all actions

Data persists across browser sessions. To clear all data, open browser DevTools and run:
```javascript
localStorage.removeItem('teamManagerState');
location.reload();
```

## Data Models

```javascript
// Project
{
  id: "uuid",
  name: "string",
  description: "string",
  status: "active" | "on-hold" | "completed" | "archived",
  dueDate: "YYYY-MM-DD",
  memberIds: ["uuid", ...],
  createdAt: "ISO string"
}

// Task
{
  id: "uuid",
  title: "string",
  description: "string",
  projectId: "uuid",
  assigneeId: "uuid" | null,
  status: "todo" | "inprogress" | "inreview" | "done",
  priority: "low" | "medium" | "high" | "critical",
  dueDate: "YYYY-MM-DD",
  createdAt: "ISO string",
  updatedAt: "ISO string"
}

// Member
{
  id: "uuid",
  name: "string",
  role: "string",
  email: "string",
  color: "#hex"
}

// Activity
{
  id: "uuid",
  action: "string",
  timestamp: "ISO string",
  entityType: "task" | "project" | "member"
}
```

## Navigation

| View | Hash | Description |
|------|------|-------------|
| Dashboard | `#dashboard` | Overview with metrics and activity |
| Projects | `#projects` | All projects grid |
| Project Detail | `#project/:id` | Kanban board for specific project |
| Tasks | `#tasks` | Full task list with filters |
| Team | `#team` | Team members overview |
| Analytics | `#analytics` | Charts and statistics |

## Keyboard Shortcuts

- Click `+` button (bottom right) to quickly add a new task
- Use global search in header to find tasks, projects, or members

## Browser Support

- Chrome 80+
- Firefox 75+
- Edge 80+
- Safari 13+

## License

MIT License — feel free to use this project for learning or as a starting point for your own applications.
