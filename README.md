quizbot/
├── database/            Shared async MongoDB layer
│   ├── db.py             Motor connection manager + automatic index setup
│   └── repositories.py   One repository class per domain (users, quizzes, payments, ...)
│
├── shared/               Code shared by both bots
│   ├── config.py          All configuration & secrets, loaded from .env
│   ├── utils/             Text cleanup, premium checks, async file I/O
│   └── html/              Quiz-report HTML generator (exam UI + analysis)
│
├── creator_bot/          Pyrogram bot — quiz creation, editing, batches, payments
│   ├── bot.py             Client setup + run_creator_bot()
│   └── handlers/          One module per feature area
│
├── runner_bot/           python-telegram-bot bot — playing quizzes, AI generation
│   ├── bot.py             Application setup + run_runner_bot()
│   └── handlers/          One module per feature area
│
└── mini_app/             FastAPI Mini App — the visual "Play" quiz player
    ├── telegram_auth.py   Verifies Telegram WebApp initData (HMAC-SHA256)
    ├── player_service.py  Play-session state, scoring, DB persistence
    ├── routes.py          FastAPI app + /api/* endpoints
    └── static/index.html  Single-file frontend (practice + exam mode UI)

run.py                  Combined launcher — starts both bots (+ Mini App, if configured)
requirements.txt
Procfile                 Heroku process declaration (single web dyno)
Dockerfile / docker-compose.yml
.env.example             Environment variable template
