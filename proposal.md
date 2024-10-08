
# **Project Proposal: Home Automation Dashboard**

### **Description:**
The **Home Automation Dashboard** is a web-based platform that enables users to control and automate smart home devices from a single interface. Users can manage devices like lights, thermostats, and cameras, create automation rules, and monitor device activities. Integration with **Amazon Alexa** will allow voice control, while **OpenWeatherMap API** will enable weather-based automations. The focus will be on secure and scalable backend development with a responsive frontend.

### **Stack:**
- **Frontend**: React.js for responsive UI.
- **Backend**: Node.js with Express for the API.
- **Database**: PostgreSQL (using **pg** for SQL queries).
- **APIs**: 
  - **Amazon Alexa API** for voice commands.
  - **OpenWeatherMap API** for weather-triggered automations.
- **Authentication**: JSON Web Tokens (JWT) for user sessions.

### **Focus:**
This is an **evenly focused full-stack application**. The backend will handle API integration and real-time control of devices, while the frontend will provide a user-friendly dashboard.

### **Type:**
The project will be a **website**, optimized for desktop and tablet use.

### **Goal:**
To provide a platform where users can:
- Manage smart devices.
- Create automation rules based on time or weather.
- Control devices via **Amazon Alexa** voice commands.

### **Users:**
The target users are **tech-savvy homeowners and renters** (aged 25-50) with smart home devices, seeking to simplify and automate their home management.

### **Data:**
- **User Data**: Devices, automations, and logs will be stored in PostgreSQL.
- **Third-Party Data**: Weather data from **OpenWeatherMap** and control integration with **Amazon Alexa**.

---

### **Challenges:**
- **API Reliability**: Handling outages, rate limits, or latency from **Alexa** and **OpenWeatherMap** APIs.
- **Data Security**: Protecting sensitive user data (passwords, device controls) with hashing and encryption.
- **Synchronization**: Ensuring real-time status updates between backend and third-party APIs.

### **Functionality:**
- **User Authentication**: JWT-secured login and registration.
- **Device Management**: Add, view, control devices.
- **Automation Setup**: Create automations based on triggers (time, weather).
- **Voice Control**: Use **Alexa** for voice commands.
- **Real-Time Monitoring**: View logs of device activity.

### **Stretch Goals:**
- **Energy Efficiency Reports**: Insight into device usage and energy consumption.
- **Mobile App**: A mobile version using **React Native**.
  
---

### **Database Schema:**
The schema will include key tables:

- **Users**: Store user info (name, email, password).
```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL
);
```
- **Devices**: Store info about user devices.
```sql
CREATE TABLE devices (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  type VARCHAR(50),
  status VARCHAR(50),
  user_id INTEGER REFERENCES users(id) ON DELETE CASCADE
);
```
- **Automations**: Define automation rules.
```sql
CREATE TABLE automations (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  trigger_type VARCHAR(50),
  trigger_value VARCHAR(100),
  action VARCHAR(100),
  device_id INTEGER REFERENCES devices(id)
);
```
- **Logs**: Track device actions.
```sql
CREATE TABLE logs (
  id SERIAL PRIMARY KEY,
  device_id INTEGER REFERENCES devices(id),
  action VARCHAR(100),
  timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

### **Issues with the API:**
- **Third-Party API Reliance**: Ensuring availability of **Alexa** and **OpenWeatherMap**.
- **API Errors**: Handle network failures or incorrect parameters with error handling.
- **Data Consistency**: Ensuring reliable real-time synchronization between device statuses and third-party APIs.

---

### **User Flow:**
1. **User Registration/Login**: JWT-secured process for access.
2. **Device Management**: Dashboard to control devices, view status.
3. **Automation Setup**: Create automation rules (time or weather-based).
4. **Voice Control**: Use **Alexa** to issue commands.
5. **Logs and Monitoring**: View device activity history.

---

### **What Makes It More Than a CRUD App?**
- **Real-Time Control**: Users control physical devices in real time.
- **Automation**: Users create complex workflows with automation triggers.
- **Alexa Integration**: Adds voice command functionality.



