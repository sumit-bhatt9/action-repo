# README.md

```markdown
# 📦 Techstax Assignment – GitHub Action Repo (Webhook Trigger)

This repository is used to simulate GitHub activity such as push, pull request, and merge events. These events trigger a webhook configured in GitHub settings, sending payloads to the Flask-based receiver app hosted in the webhook-repo.

---

## 🔗 Webhook Configuration

A webhook is configured in this repo to send events to the following endpoint:

https\://<your-ngrok-subdomain>.ngrok-free.app/webhook/receiver

```

You can update this under:

```

GitHub → Settings → Webhooks

````

Make sure to select:

- Content Type: application/json
- Trigger events:  
  ✅ Push  
  ✅ Pull Requests  
  ✅ (Optional) Merge — happens automatically on PR merge

---

## 💡 Purpose

This repository is a dummy GitHub repo meant to:

- Trigger push events using file edits and commits
- Create branches for pull requests
- Merge PRs to test the "merged" event handling

---

## 📁 Sample Trigger Files

These files were committed to simulate various actions:

- trigger.txt  
- trigger2.txt  
- trigger-final-test.txt  
- trigger-pr.txt  
- trigger-merge.txt  

Each commit and push to main or feature branches automatically hits the webhook endpoint and is captured by the webhook-repo Flask app.

---

## 🧪 Test Sequence

To test the webhook integration:

1. Create a new file:

```bash
echo "webhook test" >> trigger7.txt
````

2. Commit and push:

```bash
git add .
git commit -m "Testing webhook trigger again"
git push origin main
```

3. Create a PR via GitHub UI
4. Merge the PR
5. Check your Flask terminal and frontend UI for updated events.

---

## 🔗 Related Repo

Receiver App →
[https://github.com/sumit-bhatt9/webhook-repo](https://github.com/sumit-bhatt9/webhook-repo)

This Flask app handles the POST requests from this repo and stores the events in MongoDB.
