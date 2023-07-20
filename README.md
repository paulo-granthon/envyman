# Envyman

Envyman is a Bash script that helps you manage environment variable configurations easily. It allows you to add, start, stop, and list configuration files, configure where you want to store your configurations and track active configurations.

<h2 align="center">Features</h2>

- Create configuration files containing a set `name=value` environment variables that are loaded inside any terminal session.
- Start using the environment variables by specifying what configuration file you you want to load.
- Stop using the environment variable configuration at any time.
- Configure the root path where your configuration files are stored, moving any files inside the previous directory to the new one.
- List all configuration files in the root path.
- Check the last loaded configuration file, echoing it's full path and if it is active or not by verifying if the values of the variables defined in the file are correclty loaded into the system.
- Reinstall Envyman. If you made any changes to the script, you can imediatelly apply them by the install command.
- Uninstall Envyman, removing any modifications made to the system by the original install command and also removing your configuration files if you want to.

<h2 align="center">Getting Started</h2>

### Example workflow

Let's say you want to access the values of `URL`, `USERNAME` and `PASSWORD` from within a project that loads environment variables:

Example Spring project `application.properties`:
```properties
spring.datasource.url=${URL}
spring.datasource.username=${USERNAME}
spring.datasource.password=${PASSWORD}
```

#### Createa a configuration file for this project:

```properties
envyman add myConfigFile URL=localhost USERNAME=paulo PASSWORD=granthon
```
- Result: This will create the `myConfigFile.sh` inside the current envyman root (default: `~/envyman/`):

`~/envyman/myConfigFile.sh`:
```properties
URL=localhost
USERNAME=paulo
PASSWORD=granthon
```

#### Load the variables:
```properties
envyman start myConfigFile
```
- Result: Now the variables `URL`, `USERNAME` and `PASSWORD` are accessible to your project and will be populated at runtime with the values inside `myconfigfile`

#### "I'm working on another project and the environment variables I need are different"
```properties
envyman start myOtherConfig
```

<h2 align="center">Installation</h2>

### Prerequisites

- An Unix system such as Linux or macOS
- Bash (version 4 or above)

### Option A: TL;DR

1. Run this on any terminal of your choice to imediatelly clone and install Envyman:

    ```console
    git clone https://github.com/paulo-granthon/envyman.git
    chmod +x envyman/envyman
    envyman/envyman install
    ```

### Option B: To install Envyman, you can follow these steps:

1. Clone the Envyman repository:
    ```console
    git clone https://github.com/paulo-granthon/envyman.git
    ```

2. Move into the Envyman directory:
    ```console
    cd envyman
    ```

3. Make the script executable:
    ```console
    chmod +x envyman
    ```

4. Install Envyman:
    ```console
    ./envyman install
    ```

5. Verify the installation by running the following command:
    ```console
    envyman
    ```

<h2 align="center">Usage</h2>

Envyman supports the following commands:

- `add`: Add environment variable configuration
    ```console
    envyman add [config_file] [VAR1=VALUE1 VAR2=VALUE2 ...]
    ```

- `start`: Start using the environment variable configuration
    ```console
    envyman start [config_file]
    ```
    - Note: If you created your file in a subdirectory inside the root, you'll need to specify it with the start command

- `stop`: Stop using the environment variable configuration
    ```console
    envyman stop
    ```

- `root`: Set the root path for configuration files
    ```console
    envyman root [path]
    ```

- `ls`: List all configuration files in the root path
    ```console
    envyman ls
    ```

- `groot`: Echo the current root path
    ```console
    envyman groot
    ```

- `check`: Check configuration and print loaded file
    ```console
    envyman check
    ```

- `install`: Install Envyman
    ```console
    envyman install
    ```

- `uninstall`: Uninstall Envyman
    ```console
    envyman uninstall
    ```

<h2 align="center">Story Time</h2>

Envyman was born out of a personal need to address a specific challenge I encountered while collaborating on a team project using Spring Boot JPA. As the sole user of NeoVim (and Arch Linux by the way), I lacked a convenient IDE solution for managing local environment variables like Eclipse offered. I didn't want to abruptly switch to Eclipse or resort to hardcoding the database URL, username, and password in either the project's `application.properties` file (to avoid dealing with adding it to .gitignore since the file follows an specific template, or the risk of inadvertently exposing sensitive data on GitHub) or my machine's .bashrc file, which would require cleanup afterward. In response, I conceived the idea of creating an *environment variable manager*, **Envyman**, as a more robust solution to this issue. It provides a straightforward command to create sets of environment variables that can be easily loaded, allowing me to work on different projects with distinct variable configurations. When no longer needed, these configurations can be easily removed.  

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! If you find any issues or have suggestions, please open an [issue](https://github.com/paulo-granthon/envyman/issues/new) or a pull request on the [Envyman repository](https://github.com/paulo-granthon/envyman).

