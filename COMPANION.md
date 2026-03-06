# QA UI Skill — Usage Guide & Examples

This document shows you how to get the most out of the QA UI skill with real examples and best practices.

---

## 🎯 Quick Start

**Minimum:** Just give Copilot a URL
```
Check my app at https://myapp.vercel.app
```

**Better:** Add context about what you're building
```
QA my SaaS onboarding flow before we let beta users in. 
It's at https://staging.myapp.com
```

**Best:** Ask specific questions
```
Walk through my product and tell me what's broken
URL: https://myapp.vercel.app/checkout
```

---

## 📋 Prompt Variations

### For Landing Pages
```
Review my landing page. Is the value proposition clear? 
URL: https://myproduct.com
```

### For Sign-Up Flows
```
QA the sign-up experience. Can a new user create an account without getting stuck?
URL: http://localhost:3000/signup
```

### For Internal Tools
```
Check my admin dashboard. Are the key workflows intuitive?
URL: https://app.mycompany.com
```

### For E-Commerce
```
Walk through the purchase flow. Are there any friction points?
URL: https://shop.example.com/products
```

### For Mobile-First Apps
```
Mobile-first review: Does this work on a phone? 
URL: https://myapp.vercel.app
```

### For Post-Launch
```
Post-launch review of my app. What should I fix first?
URL: https://production.app.com
```

---

## 🎬 Full Example: Reviewing a SaaS App

**Your Prompt:**
```
I'm launching my task management app in 48 hours. 
Can you walk through the core flow and tell me what's broken?
It's at https://tasks-app-staging.vercel.app

Key workflows:
1. Sign up
2. Create a team
3. Add a task
4. Invite a teammate

Tell me what will break user trust or cause churn.
```

**The Skill Will:**
1. Open the app
2. Create a test account
3. Follow your exact workflows
4. Try edge cases (invite invalid email, create task with no title, etc.)
5. Screenshot problems
6. Deliver a report with priorities

**Example Report:**
```
**Overall Verdict:** Fix these first (3 blockers found)

**First Impression**
Clean, modern interface. Value prop is clear. Good start.

---

**🔴 Fix Before Launch**

> **Can't invite teammates after creating team**
> Where: Team settings → Invite members
> What happens: "Invite" button is disabled. No explanation why.
> Why it matters: Your core feature (collaboration) is broken. Users will churn immediately.
> Fix: Remove the disabled state or show "Invite members after team setup" if there's a reason for the delay.

> **Email validation is missing**
> Where: Invite form
> What happens: You can invite "notanemail" and form submits. User never gets the invite.
> Why it matters: Users think teammates are invited when they're not. Confusion + support tickets.
> Fix: Add email validation before submit. Show "Please enter a valid email" if needed.

> **No confirmation before deleting a task**
> Where: Task list → Delete button
> What happens: Click delete, task disappears immediately. No undo.
> Why it matters: One accidental click and hours of work are gone. Users will panic.
> Fix: Add a confirmation modal: "Delete this task? This can't be undone."

---

**🟡 Fix Soon**

> **Invite link doesn't work for non-team-members**
> Where: Shared team invite link
> What happens: If a user isn't logged in, clicking the link is confusing. They're redirected to login but forget what they were doing.
> Why it matters: Some invites will bounce. Slows team adoption.
> Fix: After login, automatically resume the team invite flow.

> **No loading state when creating a team**
> Where: "Create team" form
> What happens: You click submit, nothing happens for 2 seconds. Unclear if it's working.
> Why it matters: Impatient users click again (duplicate teams) or think it froze.
> Fix: Show a spinner. Disable the button. Add "Creating team..." text.

---

**🟢 Nice to Have**

> **Empty state could be more helpful**
> When you have no tasks, the screen just says "No tasks yet."
> Add: "Get started by [+ Add task]" to make the next action obvious.

> **Onboarding could be smoother**
> Consider a quick walkthrough on first login. Show where to create tasks, invite teammates, etc.
```

---

## 🎓 Pro Tips

### 1. Be Specific About Your Goals
❌ "Review my app"
✅ "Review the checkout flow. Will users abandon? Focus on clarity and trust."

### 2. Mention Your Users
❌ Generic review
✅ "My users are non-technical founders. Will they understand the dashboard?"

### 3. Ask for Specific Perspectives
❌ General QA
✅ "Review this from a brand-new user's perspective. Would they know what to do?"

### 4. Provide Context About Timing
❌ Just a URL
✅ "We're launching to 10K beta users in a week. What will kill adoption?"

### 5. Test Specific Workflows
❌ Just browse
✅ "Walk through: sign up → create project → invite teammate → assign task. Focus on friction."

---

## 🔄 Iterative Reviews

### First Review (Concept Check)
```
I have a prototype. Does the core flow make sense?
Is the user
