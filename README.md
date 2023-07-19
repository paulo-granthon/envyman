# Envyman

Envyman is a Bash script that helps you manage environment variable configurations easily. It allows you to add, start, stop, and list configuration files, configure where you want to store your configurations and check the current active configuration.

## Story Time

Envyman was born out of a personal need to address a specific challenge I encountered while collaborating on a team project using Spring Boot JPA. As the sole user of NeoVim (and Arch Linux by the way), I lacked a convenient IDE solution for managing local environment variables like Eclipse offered. I didn't want to abruptly switch to Eclipse or resort to hardcoding the database URL, username, and password in either the project's application.properties file (to avoid dealing with adding it to .gitignore since the file follows an specific template, or the risk of inadvertently exposing sensitive data on GitHub) or my machine's .bashrc file, which would require cleanup afterward. In response, I conceived the idea of creating an *environment variable manager*, **Envyman**, to effortlessly tackle this issue. It provides a straightforward command to create sets of environment variables that can be easily loaded, allowing me to work on different projects with distinct variable configurations. When no longer needed, these configurations can be easily removed. Envyman offers a seamless solution to my problem, empowering me to streamline my workflow efficiently and securely.

## Features

- Create configuration files with `name=value` environment variables that are loaded inside any terminal session.
- Start using the environment variables by specifying what configuration file you you want to load.
- Stop using the environment variable configuration at any time.
- Configure the root path where your configuration files are stored, moving any files inside the previous directory to the new one.
- List all configuration files in the root path.
- Check the last loaded configuration file, echoing it's full path and if it is active or not by verifying if the values of the variables defined in the file are correclty loaded into the system.
- Reinstall Envyman. If you made any changes to the script, you can imediatelly apply them by the install command.
- Uninstall Envyman, removing any modifications made to the system by the original install command and also removing your configuration files if you want to.

## Getting Started

### Prerequisites

- An Unix system such as Linux or macOS
- Bash (version 4 or above)

### Installation

#### Option A: TL;DR

1. Run this on any terminal of your choice to imediatelly clone and install Envyman:

    ```bash
    git clone https://github.com/paulo-granthon/envyman.git
    chmod +x envyman/envyman
    envyman/envyman install
    ```

#### Option B: To install Envyman, you can follow these steps:

1. Clone the Envyman repository:

    ```bash
    git clone https://github.com/paulo-granthon/envyman.git
    ```

2. Move into the Envyman directory:

    ```bash
    cd envyman
    ```

3. Make the script executable:

    ```bash
    chmod +x envyman
    ```

4. Install Envyman:

    ```bash
    ./envyman install
    ```

5. Verify the installation by running the following command:

    ```bash
    envyman
    ```

### Usage

Envyman supports the following commands:

- `add`: Add environment variable configuration
    ```bash
    envyman add [config_file] [VAR1=VALUE1 VAR2=VALUE2 ...]
    ```

- `start`: Start using the environment variable configuration
    ```bash
    envyman start [path]
    ```

- `stop`: Stop using the environment variable configuration
    ```bash
    envyman stop
    ```

- `root`: Set the root path for configuration files
    ```bash
    envyman root [path]
    ```

- `ls`: List all configuration files in the root path
    ```bash
    envyman ls
    ```

- `groot`: Echo the current root path
    ```bash
    envyman groot
    ```

- `check`: Check configuration and print loaded file
    ```bash
    envyman check
    ```

- `install`: Install Envyman
    ```bash
    envyman install
    ```

- `uninstall`: Uninstall Envyman
    ```bash
    envyman uninstall
    ```

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! If you find any issues or have suggestions, please open an [issue](https://github.com/paulo-granthon/envyman/issues/new) or a pull request on the [Envyman repository](https://github.com/paulo-granthon/envyman).

