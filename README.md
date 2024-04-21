# Matomo Server Setup Using Docker Compose

This guide walks you through setting up a Matomo analytics server using the repository at https://github.com/bowen31337/matomo-docker-compose.

## Steps to Use

1. **Clone the Repository**
   ```bash
   git clone https://github.com/bowen31337/matomo-docker-compose
   ```
2. **Run Docker Compose**
   Navigate to the cloned directory and run:

   ```bash
   docker-compose up
   ```

3. **Set Up Matomo Server**
   After the containers are up, visit the exposed Matomo URL to configure your Matomo server according to the setup wizard.

4. **Generate a Tracking Script**
   In the Matomo dashboard, generate a JavaScript tracking script for your website.
   sample of tracking script

   ```js
       <!-- Matomo -->
    <script>
      var _paq = (window._paq = window._paq || []);
      /* tracker methods like "setCustomDimension" should be called before "trackPageView" */
      _paq.push(["trackPageView"]);
      _paq.push(["enableLinkTracking"]);
      (function () {
        var u = "//localhost:8080/";
        _paq.push(["setTrackerUrl", u + "matomo.php"]);
        _paq.push(["setSiteId", "1"]);
        var d = document,
          g = d.createElement("script"),
          s = d.getElementsByTagName("script")[0];
        g.async = true;
        g.src = u + "matomo.js";
        s.parentNode.insertBefore(g, s);
      })();
    </script>
    <!-- End Matomo Code -->
   ```

5. **Create a Local Test Server**
   Use Create React App (CRA) to set up a local server:

   ```bash
   npx create-react-app test-server
   cd test-server
   ```

6. **Embed the Tracking Script**
   Paste the tracking script into the `<head>` tag of the `public/index.html` in your CRA project.

7. **Run the CRA Server**

   ```bash
   npm start
   ```

8. **Verify Installation**
   Access your local server's URL, and then go to the Matomo dashboard to view the traffic data being recorded.

For more detailed instructions, see the individual configuration files and scripts within the repository.
