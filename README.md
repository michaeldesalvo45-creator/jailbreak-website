<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Submit a Link</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #111827;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    width: 90%;
    max-width: 700px;
    background: #1f2937;
    padding: 25px;
    border-radius: 12px;
}

textarea {
    width: 100%;
    height: 220px;
    padding: 12px;
    font-size: 16px;
    border-radius: 8px;
    border: none;
    resize: vertical;
    margin-bottom: 15px;
}

button {
    background: #2563eb;
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background: #1d4ed8;
}

#status {
    margin-top: 15px;
}
</style>
</head>

<body>

<div class="container">
<h2>Submit a Link</h2>

<textarea
id="textbox"
placeholder="Paste your link or text here..."
></textarea>

<button onclick="submitForm()">Send</button>

<p id="status"></p>

</div>

<script>
async function submitForm() {
    const text = document.getElementById("textbox").value;

    if (!text.trim()) {
        document.getElementById("status").textContent = "Please enter something.";
        return;
    }

    // Replace with your backend URL
    await fetch("https://your-server.com/api/submit", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify({
            submission: text
        })
    });

    document.getElementById("status").textContent = "Submitted!";
    document.getElementById("textbox").value = "";
}
</script>

</body>
</html>
