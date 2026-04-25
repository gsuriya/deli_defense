# Deli Defense

CCTV-style threat detection that actually does something. Point a webcam (or upload a clip), it runs realtime object detection + GPT-4o scene analysis, and when something sketchy happens it fires whatever workflow you wired up — Slack, Gmail, SMS, or a Vapi voice call.

Built in one night. Vibe-coded.

## Run it

```bash
npm install
npm run dev          # frontend (vite, :5173)
node server/index.js # backend (express, :3001)
```

Needs a `.env.local` with `VITE_OPENAI_API_KEY`, `VAPI_PRIVATE_KEY`, `VAPI_PHONE_NUMBER_ID`, `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `SLACK_BOT_TOKEN`, and `TWILIO_*` if you want SMS.

## Stack

- Vite + React + TS, Tailwind, shadcn-style components
- TensorFlow.js `coco-ssd` + GPT-4o for detection & scene context
- ReactFlow for the drag-n-drop workflow builder
- Express backend wired up to Vapi, Slack, Nodemailer + Google OAuth, and Twilio

## Workflow

Drag triggers → conditions → actions onto the canvas, connect them, hit **Activate**. When a detection matches your trigger, the engine BFS-walks the graph and fires every action in parallel.

Currently supported actions: Slack message, Gmail send, SMS via Twilio, Vapi phone call.

## Built by

- [@gsuriya](https://github.com/gsuriya)
- [@mihirgan06](https://github.com/mihirgan06)
- [@yash-pandya9798](https://github.com/yash-pandya9798)
