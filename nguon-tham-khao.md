---
layout: null
---

<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Nguồn thông tin / Information Sources</title>
</head>
<body>
  <p id="message">Đang chuyển đến trang nguồn thông tin...</p>
  <p>
    <a id="fallback" href="https://anhtt92-cloud.github.io/luong-quan-nhan-privacy/#sources">
      Bấm vào đây nếu trang không tự chuyển / Click here if you are not redirected automatically
    </a>
  </p>

  <script>
    (function () {
      const params = new URLSearchParams(window.location.search);
      const queryLanguage = params.get("lang");
      let storedLanguage = null;

      try {
        const value = localStorage.getItem("legal_language");
        storedLanguage = value === "vi" || value === "en" ? value : null;
      } catch (error) {
        storedLanguage = null;
      }

      const browserLanguage = (navigator.language || "vi").toLowerCase().startsWith("vi") ? "vi" : "en";
      const language =
        queryLanguage === "vi" || queryLanguage === "en"
          ? queryLanguage
          : storedLanguage || browserLanguage;

      const target =
        "https://anhtt92-cloud.github.io/luong-quan-nhan-privacy/?lang=" +
        encodeURIComponent(language) +
        "#sources";

      document.getElementById("fallback").href = target;
      document.getElementById("message").textContent =
        language === "en" ? "Redirecting to information sources..." : "Đang chuyển đến trang nguồn thông tin...";

      window.location.replace(target);
    })();
  </script>
</body>
</html>
