🌐 Full Stack Sample Project – Jira ↔ GoRace Integration Middleware

This project implements a **lightweight full stack architecture**, acting as a **backend middleware** that connects **Jira's event system** with the **GoRace gamification platform**.  
There is **no traditional frontend**; instead, the server acts as a real-time translator of events into meaningful actions within GoRace.

---

## 🧩 Languages & Technologies Used

- 🟨 **JavaScript (ES6+)**: Main language for server-side logic  
- 🟩 **Node.js**: Backend runtime to handle asynchronous events and HTTP requests  
- ⚙️ **Express**: Framework to expose the HTTP server  
- 🌐 **Axios**: HTTP client for making requests to external APIs (GoRace)  
- 🔐 **Dotenv**: Manages sensitive environment variables like the JWT token  
- 🌍 **Ngrok**: Tunnels the local server to the internet over HTTPS for webhook testing

---

## 🖥️ Backend Server Overview

The backend server is implemented in `index.js`, and is the **core** of the integration system. It performs the following tasks:

1. 🎧 **Listens to Jira webhooks**: Receives events such as task creation, status updates, and comments  
2. 🧠 **Processes the webhook payload**: Extracts key information from the received JSON (e.g. user, issue, status)  
3. 🔄 **Maps users**: Converts Jira `accountId` to the user's email address required by GoRace  
4. 🚩 **Sends event flags**: Determines event type (e.g. task completed on time, late, comment added) and maps it to a difficulty level or a numeric flag  
5. 📡 **Sends data to GoRace**: Makes a `POST` request to GoRace’s API to register the event and trigger score updates

🗂️ This server is **stateless**, stores no persistent data, and has **no user interface** — it is a **pure middleware bridge** between Jira and GoRace.

---

## 🏁 What is the GoRace API?

The **GoRace API** is a RESTful interface developed by the **University of Cádiz**, used to register user activity in gamified learning environments, where participants progress as if running a race.

- 🌐 Accessible at: `https://api-gorace.uca.es`  
- 🔐 Requires a **JWT token** and IP-based access authorization  
- 📬 Events are registered via `POST` requests that include:

  - 📧 User email  
  - 🏷️ Activity name (e.g., `assignment`)  
  - 🕒 Timestamp of the event  
  - 📊 Associated variable (distance, flag, score, etc.)

---

## ⚙️ Conclusion

This project showcases a **backend-focused full stack architecture** tailored for **real-time platform integration**.  
It captures development activity in **Jira** and translates it into gamified feedback within **GoRace**, using a **lightweight, extensible Node.js server** that is easy to deploy, test, and adapt.