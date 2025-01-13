# Redis Hawk Monitoring

**Version:** 2.0  
**Author:** Aubin MIENANZAMBI  
**License:** GPLv2 or later

---

## Description

**Redis Hawk Monitoring** is an advanced WordPress plugin designed to efficiently monitor and manage your Redis cache. With an intuitive and comprehensive interface, this plugin provides you with a real-time overview of your Redis server's performance, allowing you to optimize cache usage and maintain the overall health of your WordPress environment.

### Key Features:

- **Real-Time Dashboard:** Visualize key Redis statistics, such as memory usage, number of client connections, key eviction rates, and more.
- **Cache Management:** Clear the Redis cache with a single click to ensure the freshness of cached data.
- **Configurable Alerts:** Receive personalized notifications in case of excessive memory usage or high concurrent connections.
- **Multisite Compatibility:** Efficiently manage Redis cache for multiple sites hosted on the same server using unique prefixes for each site.
- **Intelligent Fallback:** In the event of Redis unavailability, the plugin automatically switches to an internal non-persistent cache, ensuring your site remains operational without interruption.
- **User-Friendly Interface:** Enjoy a clear and easy-to-navigate interface, suitable for both novice administrators and advanced users.

---

## Installation

1. **Download:**
   - Download the **Redis Hawk Monitoring** plugin from the official WordPress plugin repository or your development space.

2. **Install via WordPress Admin:**
   - Access your WordPress dashboard.
   - Navigate to `Plugins` > `Add New`.
   - Click on `Upload Plugin`.
   - Select the plugin ZIP file and click on `Install Now`.
   - Once the installation is complete, click on `Activate Plugin`.

3. **Configuration:**
   - After activation, access the `Redis Hawk` menu in your WordPress dashboard.
   - Follow the instructions to configure Redis settings, including host, port, prefix, and database.

4. **Ensure Redis is Installed and Operational:**
   - **Before using Redis Hawk Monitoring, ensure that Redis is already installed and functioning on your server.**
   - If Redis encounters issues, you can revert to the default caching system by **simply deleting the `object-cache.php` file** from your `wp-content` directory.

---

## Configuration

To configure Redis with WordPress and Redis Hawk Monitoring, follow these steps:

1. **Edit the `wp-config.php` File:**
   - Add the following lines to your `wp-config.php` file:
     ```php
     // Enable WordPress caching
     define('WP_CACHE', true);
     
     // Redis Configuration
     define('WP_REDIS_HOST', '127.0.0.1');
     define('WP_REDIS_PORT', 6379);
     define('WP_REDIS_PREFIX', 'yoursite_'); // Replace 'yoursite_' with a unique prefix for each site
     define('WP_REDIS_DATABASE', 0); 
     ```
   - **Important:** Replace `'yoursite_'` with a unique prefix corresponding to your site's name to avoid confusion, especially if you are hosting multiple sites on the same server.

2. **Verify the Presence of `object-cache.php`:**
   - Ensure that the `object-cache.php` file is present in the `wp-content` directory. This file is essential for WordPress to utilize Redis as the object caching system.

3. **Configure Redis Hawk Monitoring:**
   - Access the `Redis Hawk` menu in your WordPress dashboard.
   - Configure the Redis settings according to your environment (host, port, prefix, etc.).
   - Set up alerts based on your preferences to be notified of any anomalies or excessive resource usage.

---

## Usage

### Redis Hawk Dashboard:

- **Overview:** Access the Redis Hawk dashboard to view real-time statistics of your Redis server.
- **Key Statistics:** Monitor memory usage, active connections, cache operations, and more.
- **Cache Management:** Use the `Clear Cache` button to swiftly purge all cached data in Redis.

### Alerts and Notifications:

- **Configure Alerts:** Set thresholds to receive notifications when memory usage is excessive or when there are too many concurrent connections.
- **Proactive Monitoring:** Stay informed about your Redis cache performance to take prompt action when needed.

### Multisite Compatibility:

- **Unique Prefixes:** Assign unique prefixes for each site in a multisite environment to prevent key conflicts in Redis.
- **Centralized Management:** Monitor and manage Redis cache for all your sites from a centralized interface.

---

## FAQ

### 1. **Can Redis Hawk Monitoring function without Redis installed?**
No, the plugin requires Redis to be installed and configured on your server to function correctly. In the event of Redis unavailability, the plugin automatically switches to an internal non-persistent cache, but for optimal performance, Redis must be operational.

### 2. **How can I customize the Redis prefix for each site in a multisite environment?**
When configuring in `wp-config.php`, define a unique prefix for each site by modifying the `WP_REDIS_PREFIX` constant. For example:
```php
define('WP_REDIS_PREFIX', 'mysite_');
