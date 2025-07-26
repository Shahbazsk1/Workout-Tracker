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
