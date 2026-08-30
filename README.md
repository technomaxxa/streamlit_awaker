# ☕ Streamlit App Keep-Alive Automation

A lightweight, automated GitHub Actions workflow designed to prevent Streamlit Community Cloud applications from hibernating. 

Streamlit automatically puts apps to sleep after a period of inactivity. This repository uses a headless Selenium browser to simulate a user visit every 4 hours, ensuring your application remains awake and instantly accessible.

---

## 🚀 Setup Instructions

You do not need to install anything on your local computer to use this project. The entire automation runs in the cloud via GitHub Actions.

### 1. Fork the Repository
1. Click the **Fork** button in the top-right corner of this repository to create a copy in your own GitHub account.
2. Leave all default settings and click **Create fork**.

### 2. Enable GitHub Actions
1. Navigate to the **Actions** tab at the top of your newly forked repository.
2. GitHub disables workflows in forked repositories by default for security. Click the green button that says **I understand my workflows, go ahead and enable them**.

### 3. Configure Your Streamlit URL
1. Navigate to the `.github/workflows/` directory and open the `wake.yml` file.
2. Click the **pencil icon** (Edit) in the top-right corner of the file viewer.
3. Scroll to the very bottom of the file and locate the `STREAMLIT_APP_URL` environment variable.
4. Replace the placeholder URL with the actual URL of your deployed Streamlit application:
   ```yaml
      - name: Run Selenium script
        run: python main.py
        env:
          STREAMLIT_APP_URL: "[https://your-app-name.streamlit.app/]

Click Commit changes to save your update.

5. Test the Automation
Return to the Actions tab.

Click on the Wake Streamlit App workflow on the left sidebar.

Click the Run workflow dropdown menu on the right side of the screen.

Click the green Run workflow button to trigger the script manually.

Wait about 30–60 seconds for the job to complete. A green checkmark indicates the headless browser successfully navigated to your app and verified it is awake.

⚙️ How It Works
Once configured, no further action is required. The wake.yml file utilizes a cron schedule (0 */4 * * *) that triggers the headless browser script exactly once every 4 hours, 24/7.

(Note: You can safely ignore any Node.js deprecation warnings in the Action logs, as GitHub automatically forces the runners onto supported versions).
