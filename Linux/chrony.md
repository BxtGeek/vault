# Configuring NTP with `chrony` on Linux

### **Step-by-Step Explanation:**

1. **Check System Date and Time**
   ```bash
   date
   ```
   Displays the current system date and time.

2. **View and Manage Time Settings with `timedatectl`**
   ```bash
   timedatectl
   ```
   Shows the current date, time, time zone, and NTP status.

3. **List Available Commands and Timezones**
   ```bash
   timedatectl --help
   timedatectl --version
   timedatectl --monitor
   timedatectl list-timezones
   ```
   - **`--help`:** Displays available options and usage.
   - **`--version`:** Shows the version of `timedatectl`.
   - **`--monitor`:** Monitors time changes in real-time.
   - **`list-timezones`:** Lists all supported time zones.

4. **Enable Automatic Time Synchronization (NTP)**
   ```bash
   timedatectl set-ntp true
   ```
   Enables NTP synchronization to keep the system time accurate automatically.

5. **Install `chrony` NTP Service**
   ```bash
   dnf install chrony
   ```
   Installs `chrony`, an NTP client and server that helps synchronize system time.

6. **Enable and Start `chronyd` Service**
   ```bash
   systemctl enable chronyd
   systemctl start chronyd
   ```
   - **`enable`:** Ensures `chronyd` starts automatically on system boot.
   - **`start`:** Starts the `chronyd` service immediately.

7. **Check the Status of `chronyd`**
   ```bash
   systemctl status chronyd
   ```
   Confirms that the `chronyd` service is running and provides details on its status.

8. **Monitor NTP Synchronization Status**
   ```bash
   chronyc tracking
   ```
   Displays the status of `chronyd`'s synchronization, showing information such as the server it is connected to, offset, and drift.

9. **Confirm NTP Status Again**
   ```bash
   timedatectl set-ntp true
   timedatectl
   ```
   Verifies that NTP is enabled and synchronizing correctly.

10. **View and Edit `chrony` Configuration File**
    ```bash
    cat /etc/chrony.conf
    ```
    Displays the configuration settings for `chrony`, which can be edited if you need to add or change NTP servers.

11. **Verify `chrony` Package Installation**
    ```bash
    rpm -qa | grep chronyd
    rpm -qa | grep chrony
    ```
    Checks if `chrony` is installed by listing related packages.

---

**Tip:** The `chrony` service is efficient and suitable for systems that are frequently suspended or on networks that have unstable connectivity. Using these commands, you can ensure your system time stays accurate, which is crucial for tasks like scheduling cron jobs or logging events.
