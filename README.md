# Lab12 Final Project

Basic Development and Operation - Lab 12 Final Work

## Team Information

| Name | GitHub | Student ID | Image | Contribution |
| --- | --- | --- | --- | --- |
| Jerry Yan | `Jarvis-Yan` | `20242174` | ![Jarvis-Yan](site/assets/jarvis-yan.png) | TODO% |
| TODO: real name | `TeRiRi114514` | TODO | ![TeRiRi114514](site/assets/teriri114514.png) | TODO% |
| TODO: real name | `djz08` | TODO | ![djz08](site/assets/djz08.png) | TODO% |

## Application URLs

- Personal website: <http://1.94.218.30/>
- Todo application: <http://1.94.218.30:8000/>
- GitHub repository: <https://github.com/Jarvis-Yan/Lab12-Final-Project-20242174>

## Project Structure

```text
.
├── .github/workflows/deploy.yml
├── Dockerfile
├── README.md
├── docker-compose.yml
└── site
    ├── assets
    └── index.html
```

## Local Run

```bash
docker compose up -d --build
```

Open:

- <http://localhost/>
- <http://localhost:8000/>

Stop:

```bash
docker compose down
```

## Dockerfile

The personal website is built with `nginx:1.27-alpine`.

```dockerfile
FROM nginx:1.27-alpine
COPY site/ /usr/share/nginx/html/
EXPOSE 80
```

## Docker Compose

The same Docker Compose deployment starts both applications on one server:

- `profile-site`: the website built from this repository, exposed on port `80`.
- `todo`: the open source Docker sample `dockersamples/todo-list-app`, exposed on port `8000`.
- `todo-db`: the MySQL database used by the todo application.

Todo application source:

- <https://github.com/dockersamples/todo-list-app>
- Local project copy: `vendor/todo-list-app`

## GitHub Actions Deployment

The workflow in `.github/workflows/deploy.yml` deploys on every push to `main`.

Required repository secrets:

| Secret | Value |
| --- | --- |
| `SERVER_HOST` | `1.94.218.30` |
| `SERVER_USER` | `root` |
| `SERVER_APP_DIR` | `/opt/lab12-final-project-20242174` |
| `SERVER_SSH_KEY` | Private SSH key used only for deployment |
| `SITE_URL` | `http://1.94.218.30/` |
| `TODO_URL` | `http://1.94.218.30:8000/` |

Deployment command executed by the workflow:

```bash
docker compose up -d --build
```

## Submission Checklist

- [x] Create GitHub repository.
- [x] Create personal/team website.
- [x] Add member images.
- [x] Add Dockerfile.
- [x] Add GitHub workflow.
- [x] Add Docker Compose file.
- [x] Include todo application in Docker Compose.
- [ ] Replace TODO member names, student IDs, and contribution percentages.
- [ ] Confirm repository is public.
- [ ] Deploy both applications to the server.
- [ ] Record the process as `.mp4`.
- [ ] Submit GitHub URL and video file or video URL.
