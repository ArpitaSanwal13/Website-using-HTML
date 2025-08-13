<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Reuniting with the Friends</title>
    <style>
        body, html {
            margin: 0; padding: 0; height: 100%; font-family: Arial, sans-serif;
        }
        #header {
            background-color: #4CAF50;
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
        }
        #container {
            display: flex;
            height: calc(100% - 60px); /* 60px header */
        }
        #nav {
            width: 200px;
            background-color: #f4f4f4;
            border-right: 1px solid #ddd;
            padding: 10px;
            box-sizing: border-box;
        }
        #nav a {
            display: block;
            color: #333;
            padding: 10px;
            text-decoration: none;
            margin-bottom: 5px;
            border-radius: 4px;
        }
        #nav a:hover {
            background-color: #ddd;
        }
        #content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        form label {
            display: block;
            margin-top: 10px;
            font-weight: bold;
        }
        form input, form textarea, form select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            box-sizing: border-box;
        }
        form button {
            margin-top: 15px;
            padding: 10px 15px;
            background-color: #4CAF50;
            border: none;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border-radius: 4px;
        }
        form button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div id="header">Reuniting with the Friends</div>
    <div id="container">
        <div id="nav">
            <a href="#" onclick="showPage('home')">Home</a>
            <a href="#" onclick="showPage('about')">About</a>
            <a href="#" onclick="showPage('contact')">Contact</a>
        </div>
        <div id="content">
            <!-- Content loaded dynamically here -->
        </div>
    </div>

    <script>
        // Content for pages
        const pages = {
            home: `
                <h2>Welcome Back!</h2>
                <p>We are excited to bring all friends back together for a wonderful reunion. Catch up, share stories, and make new memories!</p>
                <img src="https://images.unsplash.com/photo-1508214751196-bcfd4ca60f91?auto=format&fit=crop&w=800&q=80" alt="Friends Reunion" style="max-width:100%; border-radius: 8px;">
            `,
            about: `
                <h2>About the Reunion</h2>
                <p>This reunion is organized to reconnect old friends from school, college, and work. It's a great chance to revive friendships and reminisce good times.</p>
                <ul>
                    <li>Date: 25th December 2025</li>
                    <li>Time: 6:00 PM onwards</li>
                    <li>Venue: Green Park Banquet Hall</li>
                </ul>
            `,
            contact: `
                <h2>RSVP for the Reunion</h2>
                <form id="rsvpForm">
                    <label for="name">Full Name:</label>
                    <input type="text" id="name" name="name" required />

                    <label for="email">Email Address:</label>
                    <input type="email" id="email" name="email" required />

                    <label for="attendance">Will you attend?</label>
                    <select id="attendance" name="attendance" required>
                        <option value="">Select</option>
                        <option value="yes">Yes, I will be there</option>
                        <option value="no">No, I cannot make it</option>
                    </select>

                    <label for="message">Message (optional):</label>
                    <textarea id="message" name="message" rows="4" placeholder="Write a message..."></textarea>

                    <button type="submit">Submit RSVP</button>
                </form>
                <div id="response" style="margin-top: 15px; font-weight: bold;"></div>
            `
        };

        // Function to show page content
        function showPage(page) {
            const contentDiv = document.getElementById('content');
            contentDiv.innerHTML = pages[page];

            if(page === 'contact') {
                document.getElementById('rsvpForm').addEventListener('submit', function(e){
                    e.preventDefault();
                    const name = this.name.value.trim();
                    const email = this.email.value.trim();
                    const attendance = this.attendance.value;
                    const message = this.message.value.trim();

                    if(!name || !email || !attendance) {
                        alert('Please fill in all required fields.');
                        return;
                    }

                    // Simple validation passed
                    document.getElementById('response').textContent = `Thank you, ${name}! Your RSVP has been received.`;
                    this.reset();
                });
            }
        }

        // Load home page on initial load
        window.onload = () => {
            showPage('home');
        };
    </script>
</body>
</html>

