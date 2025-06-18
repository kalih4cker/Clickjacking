# Clickjacking
Clickjacking (short for "click hijacking") is a web-based attack where a user is tricked into clicking on something different from what they perceive — effectively hijacking their clicks.

### 🧠 **Simple Explanation:**

Imagine you're clicking a **"Play"** button on a video, but **behind it (invisible)** is a hidden **"Like"** button for a page or even a **“Transfer Money”** button. You think you're watching a video, but you're actually interacting with something else.

---

### 🎯 **Goal of Clickjacking:**

To **trick users into performing unintended actions** like:

* Liking a page on social media
* Enabling webcam/microphone
* Making unauthorized transactions
* Changing account settings

---

### 🛠️ **How It Works (Behind the Scenes):**

1. An attacker **loads a legitimate website** (like a bank or Facebook) inside an **invisible `<iframe>`**.
2. The attacker overlays **fake buttons** or UI elements on top.
3. When you click, your action goes to the hidden site.

---

### 🛡️ **Protection Against Clickjacking:**

#### For Developers:

* `X-Frame-Options` HTTP header:

  * `DENY` – page can’t be embedded at all.
  * `SAMEORIGIN` – only same site can embed.
* `Content-Security-Policy: frame-ancestors 'none'` – newer, more flexible.
* Frame-busting JavaScript (old, not recommended now):

  ```js
  if (top !== self) {
      top.location = self.location;
  }
  ```

#### For Users:

* Keep your browser updated.
* Use browser extensions like **NoScript** or **uBlock Origin**.

---

### 🔐 Real-World Example:

* A malicious site embeds **your bank’s login page** invisibly and tricks you into entering your credentials thinking it's their own form.
* Or, you’re tricked into clicking a **“Confirm Transfer”** button hidden under a fake game or quiz.

---
