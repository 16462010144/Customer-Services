<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Redirecting...</title>
  <script>
    // WhatsApp links array
    const links = [
      "https://wa.me/16462033052",
      "https://wa.me/12139459321",
      "https://wa.me/16462039576",
      "https://wa.me/12139459545",
      "https://wa.me/13329103642",
      "https://wa.me/16462035586",
      "https://wa.me/16462002752",
      "https://wa.me/16462062026",
      "https://wa.me/13322832421",
      "https://wa.me/13322837124"
    ];

    // Retrieve history from browser storage
    const storage = window.localStorage;
    const deviceKey = "device_id";
    const linkKey = "selected_link";

    // Generate unique device identifier
    function getDeviceId() {
      let id = storage.getItem(deviceKey);
      if (!id) {
        id = "device_" + Date.now() + "_" + Math.random().toString(36).substr(2, 10);
        storage.setItem(deviceKey, id);
      }
      return id;
    }

    // Execute automatic redirect
    function autoRedirect() {
      const deviceId = getDeviceId();
      let selectedLink = storage.getItem(`${deviceId}_${linkKey}`);

      if (!selectedLink) {
        selectedLink = links[Math.floor(Math.random() * links.length)];
        storage.setItem(`${deviceId}_${linkKey}`, selectedLink);
      }

      // Redirect immediately without delay
      window.location.href = selectedLink;
    }

    // Run redirect logic on page load
    window.onload = autoRedirect;
  </script>
</head>
<body>
  <!-- No content to ensure immediate redirect -->
</body>
</html>
