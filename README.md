<h1 align="center">नमस्ते — I'm Kushagra Garg</h1>

<p align="center">
  Final-year CS at <b>LNMIIT Jaipur</b> (Class of '27)<br/>
  <b>Amazon ML Summer School 2025</b> — top 3% nationwide · Vice Chairperson, ACM Student Chapter
</p>

<p align="center">
  <a href="https://drive.google.com/file/d/1f_pkcUxWK8U6fwhHmJGWF4EtjfGpax5K/view?usp=drive_link"><img src="https://img.shields.io/badge/Résumé-2F80ED?style=flat&logo=readdotcv&logoColor=white" alt="Resume"/></a>
  <a href="https://linkedin.com/in/kushagra-garg-6b63262aa"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="https://leetcode.com/u/kushagragarg_"><img src="https://img.shields.io/badge/LeetCode-FFA116?style=flat&logo=leetcode&logoColor=white" alt="LeetCode"/></a>
  <a href="https://codeforces.com/profile/_kushagragarg"><img src="https://img.shields.io/badge/Codeforces-1F8ACB?style=flat&logo=codeforces&logoColor=white" alt="Codeforces"/></a>
  <a href="mailto:23ucc564@lnmiit.ac.in"><img src="https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white" alt="Email"/></a>
</p>

---

I build full-stack systems, and lately the interesting half has been making LLM features behave like real software — retrieval you can measure, agents with bounded tools, human sign-off where it matters. I also spend time much closer to the metal, in C++ and ROS2.

The parts I enjoy most tend to be the unglamorous ones: the eval harness, the rate limiter, the migration. That's usually where a project stops being a demo.

**Currently** — open to SDE, full-stack and AI-engineering roles, internship or new-grad.

---

## Featured Projects

### 🎓 Sankalp — Rural Education Management System
**[Live](https://sankalp-village.vercel.app)** · **[Code](https://github.com/kushagragarg15/sankalp-village-project)**

A platform in real use by a student club that runs weekend classes at a village school. Three services — a React SPA, a Node/Express API and a Python FastAPI AI service — over a single PostgreSQL + pgvector database.

- **Attendance you can't fake from your hostel room.** A 4-digit code that rotates every 10 minutes, checked server-side against the session window, the volunteer's registration and a Haversine geofence. A request with no coordinates is refused rather than let through.
- **"Ask Sankalp"** — a LangGraph agent answering plain-language questions over live club data through 7 role-scoped tools, streamed with a visible trace of every lookup. Bounded at 6 iterations and 12s per tool, and every tool result is wrapped as *data, not instructions*, so a student named "ignore previous instructions" stays a student name.
- **A RAG lesson planner with an actual eval harness** — a 29-query golden set scored on precision@k, recall@k, MRR and false-positive rate. Running it proved the similarity threshold is a property of the embedding model, not the app: 0.75 (tuned on OpenAI) gave **21% recall** on Gemini, while 0.62 gives **100% with zero false positives**. The LLM judge also caught a plan asking for printed handouts in a school that has none.
- **Session prep is a fixed workflow, not an agent** — the task is identical every weekend, so the steps are code and the model is only asked to judge. Nothing becomes a plan until the volunteer who will teach it approves; rejections need a reason, and those reasons feed back into the admin dashboard.
- Guardrails and observability throughout: per-user sliding-window rate limits and a 150k-token daily budget in front of every LLM route, Prometheus metrics, structured pino logs, and one request id tracing a call from browser → Node → Python. 36 Jest tests against a mocked DB, plus a Docker Compose stack and an MCP server exposing the same tools to any MCP client.

`React` · `Node.js` · `Express` · `FastAPI` · `LangGraph` · `PostgreSQL + pgvector` · `Drizzle` · `Docker` · `Prometheus`

---

### 💬 Chatify — real-time messaging
**[Live](https://chatify-live-2026.vercel.app)** · **[Code](https://github.com/kushagragarg15/chatify-)**

One-to-one chat on the MERN stack, deployed as two independent services: a static React build on Vercel and an Express + Socket.IO server on Render.

- **Cross-origin auth done properly.** Sessions are HTTP-only JWT cookies that switch between `SameSite=None; Secure` and `SameSite=Lax` depending on environment, and the same cookie authenticates the Socket.IO handshake — not a separate token passed over the wire.
- **Presence and unread counts stay correct for conversations you don't have open**, because the client subscribes once per session rather than once per chat, and the server keeps a user-id → socket-id map it rebroadcasts on every change.
- Image attachments and avatars through Cloudinary with optimistic previews, Arcjet for bot detection and sliding-window rate limiting, and a mobile layout with real safe-area and on-screen-keyboard handling.

`React 19` · `Zustand` · `Node.js` · `Express 5` · `Socket.IO` · `MongoDB` · `Cloudinary` · `Tailwind`

---

### 🤖 Autonomous Surveillance Bot — B.Tech project
**[Code](https://github.com/kushagragarg15/autonomous-surveillance-bot)**

A mobile robot doing real-time object detection, written in C++ for ROS2 Humble and simulated in Gazebo Classic.

- **No Python in the hot path.** YOLOv11 is exported to ONNX and run through OpenCV's DNN module from C++14. Rewriting the original Python nodes gave ~50ms inference on CPU (15–20 FPS) and ~12ms with CUDA on a GTX 1660 (60–80 FPS).
- Two multi-threaded `rclcpp` nodes — control and recognition — with mutex-protected message passing and RAII resource handling. Confidence threshold, NMS threshold, input resolution, model path and CUDA are all runtime parameters, so swapping between the nano and extra-large models needs no rebuild.

`C++14` · `ROS2 Humble` · `YOLOv11` · `OpenCV DNN` · `Gazebo` · `CMake / Colcon`

---

## Tech

**Languages** — C++ · Python · JavaScript · SQL · Solidity · Bash
**Frontend** — React · Vite · Tailwind CSS · Zustand
**Backend** — Node.js · Express · FastAPI · Socket.IO · REST · JWT / OAuth 2.0
**Data** — PostgreSQL (+ pgvector) · MongoDB · MySQL · Drizzle ORM
**AI** — LangGraph · LangChain · RAG · retrieval &amp; generation evals · MCP
**Infra** — Docker · Prometheus · Vercel · Render · Git

---

## Beyond the code

- **Amazon ML Summer School 2025** — selected from the top 3% nationally.
- **Vice Chairperson, ACM Student Chapter @ LNMIIT** — running hackathons and campus coding events, and spending a fair amount of time convincing first-years that CP is worth the pain.
- Competitive programming on LeetCode and Codeforces; DSA is the thing I keep coming back to.

---

## 📊 GitHub

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=kushagragarg15&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&theme=transparent" alt="GitHub stats" height="165"/>
  <img src="https://streak-stats.demolab.com?user=kushagragarg15&hide_border=true&theme=transparent" alt="GitHub streak" height="165"/>
</p>

<p align="center"><i>Open to opportunities — <a href="mailto:23ucc564@lnmiit.ac.in">23ucc564@lnmiit.ac.in</a></i></p>
