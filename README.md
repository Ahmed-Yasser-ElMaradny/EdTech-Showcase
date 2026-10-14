# EdTech-Platform

A real-world Learning Management System (LMS) built for private teachers: a **student platform** (Android + Web), an **admin app** (Android), and an **SEO-friendly landing page**. It includes a secure exam system with anti-cheat, protected video and PDF content, a virtual credit system with redeemable codes, and a full admin panel for managing students.

Note: This repository is a showcase. Full source code is available on request (see Contact).

🚧 Under active development: the platform is still being developed, so some features may be incomplete or contain bugs. See Project status.

---

## Try it

| | |
|---|---|
| 📱 **Student app (APK)** | [Download from Releases](https://github.com/Ahmed-Yasser-ElMaradny/EdTech-Showcase/releases/download/v1.0/StudentHub.apk) |
| 🛠️ **Admin app (APK)** | [Download from Releases](https://github.com/Ahmed-Yasser-ElMaradny/EdTech-Showcase/releases/download/v1.0/Admin.App.apk) |
| 🔎 **Teacher Platform (Web) -> Live production product used by a real teacher** | [PAGE_LINK](https://share.google/GMvUlmbVPHTMcKJbN) |

### Demo accounts

| Role | Email | Password |
|---|---|---|
| Student | `Create Your Own Email ` | `Create Your Own Password ` | Use Sign Up To Create Your Student Account
| Admin / Secretary | `admin@demo.com` | `Demo123` |

The demo runs on a separate test environment with sample data. You can add, edit, and delete freely.

---

## Videos

| Student app | Admin app |
|---|---|
| [![Student demo](student-demo-thumbnail.png)](https://youtube.com/shorts/b3CM0iom7xA?si=uQ5DKtjUHKmarnJY) | [![Admin demo](admin-demo-thumbnail.png)](https://youtu.be/HnLhT63xntQ?si=996q_lbj1xKwO6aZ) |

## Project status

🚧 This platform is still under active development. Some features may be missing, incomplete, or contain bugs, and the demo environment may change or reset without notice.

If you notice anything missing, broken, or that could be improved, please let me know so I can fix and develop it. Feedback is very welcome, via email, LinkedIn, or by opening an Issue on this repository.

The software is provided "as is", without any warranty (see License).

---

## Features

### Student platform (Android & Web)
- **Exam system**
  - Questions with four answers, one correct answer, and an optional image.
  - Random question pool: the teacher sets how many questions each student gets (for example 20) and can add a larger bank (for example      50). Every student receives a different random set of questions from the pool.
  - Countdown timer: when time ends, the student's answers are submitted automatically (unanswered questions stay empty).
  - Result shown right after submission.
- **Anti-cheat**
  - Leaving the exam (app sent to background on Android, or switching to another tab on web) is detected.
  - First violation: the student is flagged and gets one final attempt. Second violation: the exam is locked and the student is marked as a cheater in the system.
- **Content protection**
  - Custom video player (playback speed, fullscreen) with YouTube integration.
  - PDF handouts rendered page-by-page, so the original file is never exposed (in progress).
  - Moving watermark (user name and email) over both video and PDF screens.
  - Android: `FLAG_SECURE` blocks screenshots and screen recording.
  - Web: HTML5 Canvas rendering with right-click and inspect disabled.
- **Single-device login:** logging in from more than one device blocks the account, which prevents account sharing.
- **Student profile:** personal data, grades, and parent's phone number.
- **Credit system:** top up credits by redeeming codes.

### Admin app (Android)
- Upload and manage videos, lessons, and exams (add / edit / delete).
- Live streaming to YouTube from the app.
- Questions can have an optional image. It is compressed on-device (Compressor) before uploading to Cloudinary to reduce storage costs.
- **Secretary panel ( in progress )**
  - Search students by ID, name, or email.
  - Edit any student's data manually and block / unblock accounts.
  - Per-exam reports: who submitted and each student's status (submitted, cheater, and so on).
- **Code generator:** create redeemable codes with any credit value.

### Landing page
- Static HTML + CSS page hosted on Vercel, built so Google can index it easily. It ranks first on Google for the teacher's name.

---

## Tech stack

| Area | Technologies |
|---|---|
| Language | Kotlin, JavaScript |
| UI | Jetpack Compose, HTML, CSS |
| Architecture | MVVM, Clean Architecture |
| Async | Kotlin Coroutines, Flow |
| Dependency Injection | Koin |
| Backend | Firebase Authentication, Firestore |
| Media | Cloudinary (images), YouTube (video & live streaming), Compressor (image compression) |
| Hosting | Vercel |

---

## Architecture

```mermaid
flowchart TD
    subgraph Clients
        S1["Student App (Android)"]
        S2["Student Platform (Web)"]
        A["Admin App (Android)"]
        L["Landing Page (HTML/CSS)"]
    end

    subgraph "App layers (MVVM + Clean Architecture)"
        UI["UI (Jetpack Compose)"]
        VM["ViewModel (StateFlow)"]
        UC["Domain (Use Cases)"]
        R["Repository"]
    end

    subgraph Services
        FA["Firebase Auth"]
        FS["Firestore"]
        CL["Cloudinary"]
        YT["YouTube"]
    end

    S1 --> UI
    A --> UI
    UI --> VM --> UC --> R
    R --> FA
    R --> FS
    R --> CL
    R --> YT
    S2 --> FA
    S2 --> FS
    S2 --> YT
    L -. hosted on .-> V["Vercel"]
    S2 -. hosted on .-> V
    K["Koin (DI)"] -. provides .-> VM
    K -. provides .-> R
```

---

## License

Copyright (c) 2026 Ahmed El Maradny. **All Rights Reserved.**

This repository is provided for viewing and evaluation only. Copying, modifying, redistributing, or reselling any part of the code or assets is not permitted without written permission. See [LICENSE](LICENSE).

---

## Contact

**Full source code available on request.**

- 📧 [ahmedelmaradny2006@gmail.com](mailto:ahmedelmaradny2006@gmail.com)
- 💼 [LinkedIn](https://www.linkedin.com/in/ahmed-el-maradny/)
- 🐙 [GitHub](https://github.com/Ahmed-Yasser-ElMaradny)
