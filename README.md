# My linux-setup 🚀

## Set up your shell environment for Pyenv in ubuntu

* Download `install-pyenv.sh` file and move it to `$HOME`.
* run following command from terminal with pwd as `$HOME`:
  ~~~ bash
  bash install-pyenv.sh
  ~~~
* Pyenv will store its data to `$HOME/.pyenv` by default.
  If you installed Pyenv via Git checkout, we recommend
  to set it to the same location as where you cloned it.
* Add the `pyenv` executable to your `PATH` if it's not already there
* run `eval "$(pyenv init -)"` to install `pyenv` into your shell as a shell function, enable shims and autocompletion
  * You may run `eval "$(pyenv init --path)"` instead to just enable shims, without shell integration

The below setup should work for the vast majority of users for common use cases.
See [Advanced configuration](#advanced-configuration) for details and more configuration options.

  - Stock Bash startup files vary widely between distributions in which of them source
    which, under what circumstances, in what order and what additional configuration they perform.
    As such, the most reliable way to get Pyenv in all environments is to append Pyenv
    configuration commands to both `.bashrc` (for interactive shells)
    and the profile file that Bash would use (for login shells).

    * First, add the commands to `~/.bashrc` by running the following in your terminal:

      ~~~ bash
      echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
      echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
      echo 'eval "$(pyenv init -)"' >> ~/.bashrc
      ~~~

  - Then, if you have `~/.profile`, `~/.bash_profile` or `~/.bash_login`, add the commands there as well.
    If you have none of these, add them to `~/.profile`.

    * to add to `~/.profile`:
      ~~~ bash
      echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
      echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
      echo 'eval "$(pyenv init -)"' >> ~/.profile
      ~~~

    * to add to `~/.bash_profile`:
      ~~~ bash
      echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
      echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
      echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
      ~~~

## Restart your shell

  for the `PATH` changes to take effect.

  ```sh
  exec "$SHELL"
  ```

## Set up your python version
- To check available python versions list you can run following command:
  ```
  pyenv install --list
  ```
- For example, if you want to install 3.12.0 version, you can type & run following command:
  ```
  pyenv install 3.12.0
  ```
- To see whether python version is successfully installed or not you can run following command:
  ```
  pyenv versions
  ```

## Set up your virtualenv
- Now, you're good to create a virtual environment using pyenv.
  * Replace `3.12.0` with `your installed python version`
  * Replace `myenv` with `your desired virtualenv name` you want to create
  ```
  pyenv virtualenv 3.12.0 myenv
  ```
- To check whether `myenv` is ready to use or not you can run following command:
  ```
  pyenv virtualenvs
  ```
- To activate your virtual environment you can run following command:
  * Replace `myenv` with `your virtualenv name` you want to activate
  ```
  pyenv activate myenv
  ```
- To deactivate your virtual environment you can run following command:
  ```
  pyenv deactivate
  ```

## Delete virtualenv
- Now, if you want to delete your created virtual environment you can run following command:
  * Replace `myenv` with `your virtualenv name` you want to delete
  ```
  pyenv virtualenv-delete myenv
  ```
