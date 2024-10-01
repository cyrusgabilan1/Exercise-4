<?php
  $filePath = 'feedback.txt';

  if ($_SERVER['REQUEST_METHOD'] == 'GET' && isset($_GET['feedbackMessage'])) {
      $feedbackMessage = ($_GET['feedbackMessage']) . "\n\n";
      file_put_contents($filePath, $feedbackMessage, FILE_APPEND);
      $message = "Your feedback has been added!";
  }

  if ($_SERVER['REQUEST_METHOD'] == 'POST' && isset($_POST['name']) && isset($_POST['age']) && isset($_POST['email'])) {
      $name = ($_POST['name']);
      $age = ($_POST['age']);
      $email = htmlspecialchars($_POST['email']);

      $postContent = "Name: $name, Age: $age, Email: $email\n";
      file_put_contents($filePath, $postContent, FILE_APPEND);

      $message = "Thank you, $name! Your details have been recorded!";
  }


  if (file_exists($filePath)) {
      $fileContent = file_get_contents($filePath);
  } else {
      $initialContent = "Share your thoughts about our Website!";
      file_put_contents($filePath, $initialContent);
      $fileContent = $initialContent;
  }
  ?>
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Website Feedback</title>
      <link rel="stylesheet" href="feedback.css">
  </head>
  <body>

  <header>
      <h1>Provide Your Information and Feedback</h1>
      <p>Share your details and give us feedback about our website!</p>
  </header>

  <div class="container">

      <?php if (isset($message)): ?>
          <p class="success"><?php echo $message; ?></p>
      <?php endif; ?>

      <div class="message">
          <h2>Thoughts From Our Visitors</h2>
          <pre><?php echo htmlspecialchars($fileContent); ?></pre>
      </div>

      <div class="form">
          <h2>Provide Your Information and Feedback</h2>

          <form action="" method="POST" class="post-form">
              <input type="text" name="name" placeholder="Your Name" required><br><br>
              <input type="text" name="age" placeholder="Your Age" required><br><br>
              <input type="email" name="email" placeholder="Your Email" required><br><br>
              <button type="submit" class="send">Submit Info</button>

          </form>

          <form action="" method="GET" class="get-form">
              <textarea class="message-text" name="feedbackMessage" placeholder="Your feedback about the website..." required></textarea>
              <button type="submit" class="send">Submit Feedback</button>
          </form>
      </div>

  </div>

  <footer>
      <p>&copy; 2024 Group 6. All rights reserved.</p>
      <p><a href="privacy-policy.html" class="footer-link">Privacy Policy</a> | <a href="terms-of-service.html" class="footer-link">Terms of Service</a></p>
  </footer>

  </body>
  </html>
