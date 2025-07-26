# 🏋️‍♂️ Workout Tracker
<h2>📌 Project Description</h2>
<p>This project allows you to track your daily workouts by simply typing what exercises you did (in plain English). It uses the Nutritionix API to convert your input into structured workout data (exercise name, duration, calories burned), and then stores this data in a Google Sheet using the Sheety API.</p>
<h3>🔧 Modules & Technologies Used</h3>
<ul>
  <li><strong>requests:</strong>	Makes HTTP requests to Nutritionix and Sheety APIs</li>
  <li><strong>datetime:</strong>	Captures current date and time</li>
  <li><strong>os:</strong>	(Optional) Used to store sensitive credentials like API keys via environment variables</li>
  <li><strong>json:</strong> (Handled internally by requests) for data formatting</li>
</ul>
<h3>🌐 APIs and Services Used</h3>
<h4>1. Nutritionix API</h4>
<ul>
<li><strong>Purpose:</strong> Converts natural language exercise descriptions into structured data like calories burned, duration, etc.</li>
<li><strong>Endpoint:</strong><br>
  <code>https://trackapi.nutritionix.com/v2/natural/exercise</code>
</li><br>
<li><strong>Docs:</strong><br>
  <a href="https://www.nutritionix.com/business/api" target="_blank">🔗 https://www.nutritionix.com/business/api</a>
</li>
</ul><br>
<h4>2. Sheety API</h4>
<ul>
<li><strong>Purpose:</strong> Allows updating Google Sheets like a database using RESTful API calls.</li>
<li><p><strong>Endpoint format (example):</strong><br>
  <code>https://api.sheety.co/&lt;your-project-id&gt;/&lt;project-name&gt;/&lt;sheet-name&gt;</code>
</p>
<p><strong>Your actual endpoint (from the script):</strong><br>
  <code>https://api.sheety.co/58c9bc9fcd1d4728baeba4b7be2f3c8a/myWorkouts/workouts</code></p>
</li>
<li><strong>Docs:</strong><br>
  <a href="https://sheety.co/docs" target="_blank">🔗 https://sheety.co/docs</a>
</li>
</ul>
<h3>✅ Step-by-Step Guide: Setting Up Sheety API</h3>
<p><strong>🔧 Step 1: Create a Google Sheet</strong></p>
<ol>
  <li>Go to Google Sheets.</li>
  <li>Create a new sheet and name it (e.g., myWorkouts).</li>
  <li>Create columns for the data you want to store, such as:
    <ul>
      <li>date</li>
      <li>time</li>
      <li>exercise</li>
      <li>duration</li>
      <li>calories</li>
    </ul>
  </li>
  <p>📌 Example:</p>
<table>
      <thead>
        <tr>
          <th>date</th>
          <th>time</th>
          <th>exercise</th>
          <th>duration</th>
          <th>calories</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>2025-07-25</td>
          <td>08:30</td>
          <td>Running</td>
          <td>30 min</td>
          <td>300</td>
        </tr>
        <tr>
          <td>2025-07-26</td>
          <td>07:00</td>
          <td>Cycling</td>
          <td>45 min</td>
          <td>400</td>
        </tr>
      </tbody>
    </table>
  <p>Click "Get Started for Free" or Sign in with your Google account.</p>
</ol>
<p><strong>🌐 Step 2: Go to Sheety</strong></p>
<ol>
  <li>Visit https://sheety.co.</li>
  <li>Click "Get Started for Free" or Sign in with your Google account.
</li>
</ol>
<p><strong>📁 Step 3: Create a New Project</strong></p>
<ol>
  <li>After logging in, click "New Project".</li>
  <li>Choose the Google Sheet you created.</li>
  <li>Authorize access if prompted.</li>
  <li>Give your project a name (e.g., My Workouts).</li>
</ol>
<p><strong>🔌 Step 4: Get Your API Endpoint</strong></p>
<p>Once your sheet is connected, Sheety will show your custom API endpoint.<br>

For example:<br>


 https://api.sheety.co/"your-project-id"/"project-name"/"sheet-name"

<p><strong>🔐 Step 5: Authentication Options</strong></p>
<ul>
  
<li><strong>Option 1: No Auth</strong></li>
<ul>
  <li>Anyone can access your sheet. Not secure.</li>
  <li>Just use:
    <p>response = requests.post(sheet_endpoint, json=sheet_inputs)</p>
  </li>
</ul>
<li><strong>Option 2: Basic Auth</strong></li>
<p><strong>Use your Sheety username and password:</strong></p>
<p>response = requests.post(sheet_endpoint, json=sheet_inputs, auth=("your_username", "your_password"))</p>
<li><strong>Option 3: Bearer Token (Recommended)</strong></li>
<ol>
  <li>In Sheety dashboard → Click on your project → Settings → Authentication.</li>
  <li>Enable "Bearer Token" auth.</li>
  <li>Copy the token.</li>
  <li>In your code:</li>
</ol>
<p>
headers = {<br>
    "Authorization": "Bearer YOUR_TOKEN"<br>
}<br>
response = requests.post(sheet_endpoint, json=sheet_inputs, headers=headers)
</p>
