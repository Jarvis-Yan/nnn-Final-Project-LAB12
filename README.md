# Lab12 Final Project

Basic Development and Operation - Lab 12 Final Work

## Team Information

| Name | GitHub | Student ID | Image | Contribution |
| --- | --- | --- | --- | --- |
| Jerry Yan | `Jarvis-Yan` | `20242174` | ![Jarvis-Yan](site/assets/jarvis-yan.png) | TODO% |
| Chunrui Miao | `TeRiRi114514` | `20242170` | ![TeRiRi114514](site/assets/Vergil.jpg) | TODO% |
| TODO: real name | `djz08` | TODO | ![djz08](site/assets/djz08.png) | TODO% |

## Application URLs

- Target personal website: <http://1.94.218.30:18180/>
- Target todo application: <http://1.94.218.30:18100/>
- GitHub repository: <https://github.com/Jarvis-Yan/Lab12-Final-Project-20242174>

Current deployment status: local Docker Compose and remote deployment are verified. Deployment workflow history: <https://github.com/Jarvis-Yan/Lab12-Final-Project-20242174/actions/workflows/deploy.yml>.

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

- <http://localhost:18180/>
- <http://localhost:18100/>

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

- `profile-site`: the website built from this repository, exposed on port `18180`.
- `todo`: the open source Docker sample `dockersamples/todo-list-app`, exposed on port `18100`.
- `todo-db`: the MySQL database used by the todo application.

Todo application source:

- <https://github.com/dockersamples/todo-list-app>
- Local project copy: `vendor/todo-list-app`

## GitHub Actions Deployment

The workflow in `.github/workflows/deploy.yml` deploys automatically on pushes to `main`. It can also be started manually from GitHub Actions.

Required repository secrets:

| Secret | Value |
| --- | --- |
| `SERVER_HOST` | `1.94.218.30` |
| `SERVER_USER` | `root` |
| `SERVER_SSH_PORT` | `2000` |
| `SERVER_APP_DIR` | `/opt/lab12-final-project-20242174` |
| `SERVER_SSH_KEY` | Private SSH key used only for deployment |

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
- [x] Confirm repository is public.
- [x] Deploy both applications to the server.
- [x] Prepare `.mp4` evidence video: `evidence/Lab12-Final-Project-20242174-evidence.mp4`.
- [ ] Submit GitHub URL and video file or video URL.
