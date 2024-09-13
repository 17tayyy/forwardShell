## Usage

This setup allows you to establish a forward shell using HTTP requests to execute commands on a remote system via the `index.php` file. The `forward_shell.py` script sends commands, and the `main.py` script initializes and handles the forward shell.

### Prerequisites

- A web server (e.g., Apache or Nginx) with PHP installed.
- The `index.php` file must be uploaded to the server, allowing it to execute shell commands from a `GET` request.
- Ensure the `requests` and `termcolor` Python libraries are installed:

    ```bash
    pip install requests termcolor
    ```

### Setup

1. **Deploy index.php**: Place the provided `index.php` file on the target web server in a publicly accessible directory. This script is responsible for executing shell commands sent from the forward shell.

2. **Configure forward_shell.py**: Update the `self.main_url` variable in the `forward_shell.py` script to point to the correct URL where `index.php` is hosted:

    ```python
    self.main_url = "http://<TARGET_IP>/index.php"
    ```

### Running the Shell

1. **Start the Forward Shell**: On your local machine, run the `main.py` script to start interacting with the forward shell.

    ```bash
    ./main.py
    ```

   The forward shell will be initialized, and you'll be able to send commands that are executed on the target server.

2. **Command Execution**: Once the shell is running, you can issue various commands:

    - **Run Shell Commands**: Enter any shell command and it will be executed on the target machine. The output will be displayed on your local terminal.

      Example:

      ```bash
      >>> ls -la
      ```

    - **Enum SUID**: This command lists files on the target system with SUID permissions, which may have elevated privileges.

      ```bash
      >>> enum suid
      ```

    - **Pseudo-terminal**: Start a pseudo-terminal session with the following command:

      ```bash
      >>> script /dev/null -c bash
      ```

      Once started, you'll have a more interactive session, and the system will format the output for easier use.

    - **Help**: View available helper options.

      ```bash
      >>> help
      ```

    - **Exit**: To exit the pseudo-terminal and end the session, use:

      ```bash
      >>> exit
      ```

### Example Session

Starting the shell:

```bash
./main.py
