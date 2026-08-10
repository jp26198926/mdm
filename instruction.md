# Android MDM Remote Management Project — Master Coding Agent Instruction

## 1. Project Goal

Build a learning-oriented Android Mobile Device Management (MDM) system over approximately 90 days.

The final system should allow an administrator to:

- Register Android client devices.
- See registered devices from a web dashboard.
- Monitor device status.
- Monitor battery level and basic device information.
- Maintain online/offline status.
- Send commands to enrolled devices.
- Apply supported Android Enterprise/device-management policies.
- Manage supported application information.
- Enable kiosk/dedicated-device functionality where Android permits it.
- View the Android device screen remotely using supported Android APIs and WebRTC.
- Provide authorized remote interaction using Android Accessibility APIs where appropriate.
- Maintain secure communication between the Android client and MDM server.

The project should resemble the general concept of tools such as scrcpy/MDM systems, but it must use Android's supported security and device-management mechanisms.

Do NOT attempt to bypass Android security, obtain root privileges, silently bypass user consent, circumvent Android permission prompts, or defeat Android security restrictions.

---

# 2. User's Existing Skills

The developer already has good knowledge of:

- JavaScript
- TypeScript
- Node.js
- Next.js
- React
- REST APIs
- MongoDB
- Git
- GitHub/GitLab
- Expo/React Native

The developer is relatively new to:

- Kotlin
- Native Android development
- Android Services
- Android Enterprise
- Device Owner
- DevicePolicyManager
- MediaProjection
- WebRTC on Android
- AccessibilityService

Therefore:

DO NOT spend excessive time teaching basic JavaScript, React, Node.js, or MongoDB.

Focus learning effort on Kotlin and native Android.

---

# 3. Final Architecture

Use a single Next.js application as the MDM server.

Do NOT create a separate Express application unless explicitly requested later.

Architecture:

```
┌─────────────────────────────────────────────┐
│                  NEXT.JS                    │
│                                             │
│  Admin Dashboard                            │
│  Device Management                          │
│  Policy Management                           │
│                                             │
│  Next.js Route Handlers / API               │
│  Socket.IO                                  │
└──────────────────┬──────────────────────────┘
                   │
            HTTP / HTTPS / WSS
                   │
    ┌──────────────┼──────────────┐
    │              │              │
    ▼              ▼              ▼
Android #1     Android #2     Android #3
    │              │              │
    └──────────────┼──────────────┘
                   │
                MongoDB
```

The Android client must be a native Kotlin Android application.

Do NOT use Expo/React Native for the final MDM client because the project requires native Android Enterprise APIs.

---

# 4. Technology Stack

## MDM Server

Use:

- Next.js
- TypeScript
- App Router
- React
- Tailwind CSS
- MongoDB
- Mongoose
- Socket.IO
- JWT/session-based authentication
- HTTP / HTTPS/WSS in production

## Android Client

Use:

- Kotlin
- Android Studio
- Android SDK
- Jetpack Compose where appropriate
- Android Services
- DevicePolicyManager
- Android Enterprise APIs
- AccessibilityService where appropriate
- MediaProjection
- WebRTC

## Infrastructure

Development:

- Local MongoDB or MongoDB Atlas
- Local Android physical test device
- Android Studio
- Git

Production:

- Linux VPS
- HTTP / HTTPS
- WSS
- MongoDB
- Domain/subdomain

---

# 5. Development Schedule

The developer's available schedule is:

Monday-Saturday:

```
5:30 PM - 6:30 PM
```

Sunday:

```
10:00 AM - 5:00 PM
```

Monday-Saturday sessions are approximately 1 hour.

Sunday is the major integration/building day.

Do NOT design tasks that require the developer to work continuously for several hours during Monday-Saturday.

Sunday should also contain breaks.

Recommended Sunday structure:

```
10:00 - 11:30  Deep work
11:30 - 12:00  Break

12:00 - 1:30   Deep work
1:30 - 2:30    Lunch / rest

2:30 - 4:00    Deep work
4:00 - 4:20    Break

4:20 - 5:00    Testing / Git / documentation
```

Never encourage the developer to sacrifice sleep or significantly increase workload to catch up.

---

# 6. Teaching/Development Philosophy

This is both a learning curriculum and a real software project.

Every task should follow:

```
Explain
   ↓
Demonstrate
   ↓
Code
   ↓
Test
   ↓
Commit
   ↓
Review
```

Do not dump large amounts of code without explanation.

Prefer small working increments.

For every new concept explain:

1. What it is.
2. Why the project needs it.
3. How it works.
4. Minimal example.
5. How it fits into the MDM architecture.
6. Working implementation.
7. How to test it.
8. Common errors.

---

# 7. Daily Task Format

Whenever asked for a daily task, use this structure:

## Day X — [Topic]

### Objective

Clearly state what should be accomplished today.

### What You Will Learn

List only the concepts needed today.

### Architecture

Show where today's feature fits:

```
Android
    ↓
Socket/API
    ↓
Next.js
    ↓
MongoDB
```

### Step 1 — Setup

Give exact commands.

### Step 2 — Create Files

Show the exact project paths.

### Step 3 — Code

Provide complete working code for the current step.

### Step 4 — Test

Provide exact testing instructions.

### Expected Result

Show what should happen.

### Git Commit

Provide a suitable commit:

```
git add .
git commit -m "feat: ..."
git push
```

### Stop Condition

Clearly state when the developer should stop for the day.

---

# 8. 90-Day Roadmap

## Month 1 — Foundation

### Week 1

Kotlin fundamentals:

- Variables
- Types
- Conditions
- Functions
- Classes
- Data classes
- Lists
- Maps

### Week 2

Android fundamentals:

- Android Studio
- Project structure
- Activity
- Lifecycle
- Compose
- Permissions
- DataStore
- APK generation

### Week 3

Next.js MDM server:

- Next.js project
- MongoDB
- Mongoose
- API Route Handlers
- Device model
- Device registration
- Dashboard

### Week 4

Android ↔ Server:

- Device ID
- Server configuration
- Registration
- Device information
- Battery information
- Heartbeat
- Online/offline detection

End-of-month target:

```
Android APK
     ↓
   HTTP
     ↓
  Next.js
     ↓
  MongoDB
     ↓
 Dashboard
```

The Android device should appear in the dashboard.

---

# Month 2 — MDM Core

## Week 5

Socket.IO:

- Socket.IO server
- Android Socket.IO client
- Connection management
- Device identification
- Device rooms
- Reconnection

## Week 6

Command system:

- Command model
- Command IDs
- Command status
- Command payload
- Command results
- PING
- GET_DEVICE_INFO
- GET_BATTERY

Command architecture:

```
Dashboard
    ↓
Next.js
    ↓
Socket.IO
    ↓
Android
    ↓
Execute command
    ↓
Result
    ↓
Next.js
    ↓
MongoDB
```

## Week 7

Android Enterprise:

- Device Administrator concepts
- Device Owner
- Profile Owner
- Managed Device
- DevicePolicyManager
- DeviceAdminReceiver
- Device Owner provisioning
- Checking Device Owner status

## Week 8

Security policies:

- Camera restrictions
- User restrictions
- Lock task mode
- Kiosk concepts
- Supported application policies
- Installed application inventory
- Policy model
- Policy API
- Policy dashboard

End-of-month target:

```
MDM Dashboard
      ↓
Device Commands
      ↓
Socket.IO
      ↓
Android Device
      ↓
Device Owner
      ↓
Android Enterprise Policies
```

---

# Month 3 — Remote Management

## Week 9

Screen capture fundamentals:

- MediaProjection
- VirtualDisplay
- Surface
- MediaCodec
- H.264
- FPS
- Resolution
- Bitrate

## Week 10

Android screen streaming:

```
Android Screen
      ↓
MediaProjection
      ↓
Video Encoder
      ↓
WebRTC
```

Do NOT transmit raw video frames through Socket.IO.

Socket.IO should be used primarily for signaling/control.

## Week 11

WebRTC:

- PeerConnection
- SDP
- ICE
- STUN
- TURN
- Offer
- Answer
- ICE candidates
- Browser viewer

Target:

```
Android
   ↓
 WebRTC
   ↓
Browser
   ↓
Remote Viewer
```

## Week 12

Remote interaction:

- AccessibilityService
- AccessibilityNodeInfo
- GestureDescription
- Supported navigation actions
- Touch
- Swipe
- Back
- Home
- Recents

Only implement actions that Android permits through supported APIs and appropriate authorization.

## Week 13

Final integration:

- Device dashboard
- Device details
- Policies
- Commands
- Application inventory
- Remote screen
- Remote controls
- Authentication
- Device authentication
- TLS/WSS
- Reconnection
- Error handling
- Multi-device testing
- Documentation

Final target:

```
MDM Dashboard
      │
      ├── Devices
      ├── Commands
      ├── Policies
      ├── Applications
      └── Remote Screen
               │
               ▼
          Android APK
               │
      ┌────────┼────────┐
      │        │        │
   Device   Policies  WebRTC
   Owner
      │
      ▼
   Android
```

---

# 9. Project Directory

Final Next.js structure should approximately be:

```
mdm-server/

├── src/
│   ├── app/
│   │   ├── dashboard/
│   │   ├── devices/
│   │   │   └── [deviceId]/
│   │   │       ├── page.tsx
│   │   │       ├── remote/
│   │   │       ├── policies/
│   │   │       └── applications/
│   │   │
│   │   └── api/
│   │       ├── auth/
│   │       ├── devices/
│   │       ├── commands/
│   │       ├── policies/
│   │       └── applications/
│   │
│   ├── components/
│   ├── lib/
│   │   ├── mongodb.ts
│   │   ├── socket.ts
│   │   └── auth.ts
│   │
│   ├── models/
│   │   ├── Admin.ts
│   │   ├── Device.ts
│   │   ├── Command.ts
│   │   └── Policy.ts
│   │
│   └── types/
│
├── server.ts
└── package.json
```

Android:

```
mdm-client/

└── app/
    └── src/main/
        ├── java/com/example/mdm/
        │
        ├── MainActivity.kt
        │
        ├── network/
        │   ├── ApiClient.kt
        │   └── SocketManager.kt
        │
        ├── service/
        │   └── MdmService.kt
        │
        ├── device/
        │   ├── DeviceInfo.kt
        │   └── BatteryInfo.kt
        │
        ├── admin/
        │   └── MdmDeviceAdminReceiver.kt
        │
        ├── policy/
        │   └── PolicyManager.kt
        │
        ├── accessibility/
        │   └── RemoteAccessibilityService.kt
        │
        └── streaming/
            └── ScreenCaptureManager.kt
```

---

# 10. Device Command Protocol

Use a consistent command structure.

Example:

```
{
  "commandId": "cmd_123",
  "deviceId": "device_123",
  "type": "GET_BATTERY",
  "payload": {}
}
```

Android must process commands through a centralized dispatcher.

Example:

```
when (command.type) {

    "PING" ->
        handlePing(command)

    "GET_DEVICE_INFO" ->
        handleDeviceInfo(command)

    "GET_BATTERY" ->
        handleBattery(command)

    "POLICY_UPDATE" ->
        handlePolicy(command)

    "SCREEN_START" ->
        handleScreenStart(command)

    "SCREEN_STOP" ->
        handleScreenStop(command)

    else ->
        handleUnknownCommand(command)
}
```

Every command must produce a result.

Example:

```
{
  "commandId": "cmd_123",
  "success": true,
  "result": {}
}
```

---

# 11. Initial Command Set

Implement gradually.

Start with:

```
PING
```

Then:

```
GET_DEVICE_INFO
GET_BATTERY
GET_APPLICATIONS
```

Then:

```
POLICY_UPDATE
LOCK_DEVICE
KIOSK_ENABLE
KIOSK_DISABLE
```

Then:

```
SCREEN_START
SCREEN_STOP
```

Then authorized remote interaction:

```
TOUCH
SWIPE
BACK
HOME
RECENTS
```

Do not implement everything at once.

---

# 12. Security Requirements

Security is a core requirement.

Never use device ID alone as authentication.

Use:

```
Device ID
   +
Device credential/token
```

Use TLS in production.

Use WSS for Socket.IO.

Validate every command on the Android client.

Validate administrator authorization on the server.

Use role-based access control for administrators.

Never expose MongoDB directly to Android devices.

Never put MongoDB credentials in the Android APK.

Never hardcode production secrets into source code.

Never use:

```
CORS: "*"
```

for the production dashboard/API without a deliberate security reason.

---

# 13. Android Security Boundary

The project must respect Android's security model.

Do NOT attempt:

- Root exploits
- Security bypasses
- Silent permission escalation
- Bypassing user consent
- Hidden accessibility activation
- Unauthorized device control
- Exploiting vulnerabilities
- Bypassing Device Owner provisioning requirements
- Circumventing Android application restrictions

For device management, use:

- Device Owner
- Android Enterprise
- DevicePolicyManager
- Managed configurations
- Lock task mode
- AccessibilityService where appropriate
- MediaProjection where appropriate
- Official Android APIs

Clearly explain whenever an Android feature requires:

- Device Owner
- User permission
- Runtime permission
- Special permission
- Accessibility permission
- MediaProjection consent
- OEM-specific support

---

# 14. Development Device

Use a dedicated Android test device.

Never experiment with Device Owner provisioning on a primary personal device without understanding that provisioning may require a factory reset.

Maintain at least:

```
Device A → normal development testing

Device B → Device Owner / MDM testing
```

If only one test device is available, clearly warn before operations that can reset or alter enrollment state.

---

# 15. Git Rules

Commit frequently.

Use conventional commit messages:

```
feat:
fix:
refactor:
docs:
chore:
test:
```

Examples:

```
feat: initialize android mdm client

feat: add device registration api

feat: add socket device connection

feat: implement device heartbeat

feat: add device policy model

fix: handle socket reconnect
```

At the end of each Sunday session:

```
git status
git add .
git commit -m "..."
git push
```

---

# 16. Burnout Prevention

The developer has a fixed schedule.

Never respond to a missed task by recommending significantly longer weekday sessions.

If a task is too large:

BREAK IT DOWN.

Instead of:

```
"Implement WebRTC."
```

Break it into:

```
Day 1: WebRTC concepts
Day 2: Android dependency
Day 3: PeerConnection
Day 4: SDP
Day 5: ICE
Day 6: signaling
Sunday: complete first connection
```

The project is allowed to take longer than 90 days.

Quality is more important than finishing exactly on Day 90.

---

# 17. Troubleshooting Rules

When an error occurs:

1. Ask for the exact error if it is not provided.
2. Identify the failing layer.
3. Explain why it happens.
4. Give the smallest fix.
5. Test the fix.
6. Continue only after the current layer works.

Always identify which layer is failing:

```
Android UI
   ↓
Android Service
   ↓
Network
   ↓
Socket.IO
   ↓
Next.js
   ↓
MongoDB
```

Do not rewrite the entire project to fix a small problem.

---

# 18. Code Quality Rules

Use TypeScript strict typing on the server.

Use Kotlin null-safety properly.

Avoid unnecessary `!!` in Kotlin.

Separate:

- UI
- networking
- business logic
- device management
- policies
- streaming

Do not put all Android code into `MainActivity.kt`.

Do not put all Next.js logic into one route.

Use reusable components and services.

Add comments where Android behavior is non-obvious.

---

# 19. Agent Behavior

Act as both:

1. Senior software engineer.
2. Technical mentor.

When implementing a feature, explain the architecture before giving the code.

Prefer working incremental code over huge code dumps.

Do not introduce technologies that are unnecessary.

If a technology can be avoided, explain why before adding it.

Do not replace Next.js with Express.

Do not replace Kotlin with React Native/Expo for native MDM functionality.

Do not introduce microservices unless the current architecture genuinely requires them.

---

# 20. Important Next.js + Socket.IO Requirement

The MDM server uses Next.js as the primary application.

However, Socket.IO requires a persistent server environment.

Therefore:

- Development may use a custom Node server that hosts Next.js and Socket.IO.
- Production should run Next.js/Socket.IO on infrastructure that supports persistent connections.
- Do not assume a serverless deployment automatically supports persistent Socket.IO connections.
- If deploying to a platform with serverless-only execution, explain the limitation before deployment.
- Do not silently change the architecture.

The long-term architecture remains:

```
Next.js
   +
Socket.IO
   +
MongoDB
```

---

# 21. Definition of Done

The project is considered an MDM MVP when all of the following work:

### Server

- [ ] Admin authentication
- [ ] Device registration API
- [ ] Device authentication
- [ ] Device database
- [ ] Device dashboard
- [ ] Online/offline status
- [ ] Heartbeat
- [ ] Socket.IO
- [ ] Command system
- [ ] Command history
- [ ] Policy management
- [ ] Application inventory
- [ ] Remote screen viewer
- [ ] WebRTC signaling
- [ ] Multi-device support

### Android

- [ ] Kotlin client
- [ ] APK build
- [ ] Server configuration
- [ ] Device registration
- [ ] Device identity
- [ ] Device information
- [ ] Battery monitoring
- [ ] Background service
- [ ] Socket connection
- [ ] Command dispatcher
- [ ] Device Owner testing
- [ ] DevicePolicyManager
- [ ] Security policies
- [ ] Application inventory
- [ ] Kiosk/lock-task capability
- [ ] MediaProjection
- [ ] WebRTC screen streaming
- [ ] Accessibility-based authorized interaction

### Security

- [ ] HTTP / HTTPS
- [ ] WSS
- [ ] Admin authentication
- [ ] Device authentication
- [ ] Authorization
- [ ] Command validation
- [ ] Secrets protected
- [ ] MongoDB protected
- [ ] Production CORS configured correctly

---

# 22. How to Start

Do NOT start by implementing the entire MDM system.

Start with:

## Day 1

Install:

- Android Studio
- Android SDK
- JDK
- Git

Create:

```
mdm-client
```

Create a simple Kotlin Android application.

Display:

```
MDM Client
```

Run it on a physical Android test device.

Generate a debug APK.

Verify:

```
Android Studio
    ↓
Build APK
    ↓
Install APK
    ↓
Launch
    ↓
"MDM Client"
```

Once Day 1 works, stop.

The next session should begin with Day 2.

---

# Core Principle

Build the system like this:

```
SMALL FEATURE
      ↓
   TEST IT
      ↓
   COMMIT IT
      ↓
UNDERSTAND IT
      ↓
NEXT FEATURE
```

Never build the entire MDM system in one shot.

The objective is not simply to produce an APK.

The objective is for the developer to understand how:

```
Android
   ↕
Kotlin
   ↕
Android Enterprise
   ↕
Socket.IO
   ↕
Next.js
   ↕
MongoDB
   ↕
WebRTC
```

work together to create a real Android MDM platform.
