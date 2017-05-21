# Boiler

Generic custom boilerplates

## Usage

```
boil <NAME> [TEMPLATES...]
```

## Example Configuration

Imagine you want to create a React.js project, but every time you do this, you have a series of commands you execute:

``` sh
mkdir ~/build/newreact    # where to start your new project
git init                  # this happens for every project
npm init -y               # this happens for every javascript project
npm i -S react react-dom  # this happens for every react project
```

`boil newreact js/react` can do this for you with the following configuration:

``` sh
cd ~/.config/boiler
echo "default_dir $HOME/build" > conf        # where to boil every new project
echo 'git init' > all                        # this happens for every project

Mkdir js
echo 'npm init -y' > js/all                  # this happens for every javascript project
echo 'npm i -S react react-dom' > js/react   # this happens for every react project
```

---

Multiple templates can also be specified. For example, `boil newreact js/react js/lint/react` would look for the following files in `~/.config/boiler`:

    all
    js/all
    js/react
    js/react/all
    js/react/react
    js/lint/all
    js/lint/react/all
    js/lint/react/react

## More advanced configuration

Files in `~/.config/boiler` don't have to be just single commands, they can be multiple commands, or entire scripts. All scripts are passed the project's directory as an argument.

The files in `~/.config/boiler` are, by default, executed with the user's `$SHELL`. If they are marked as executable (ie with `chmod +x`) they will be called as a regular executable, which means they can be written in any language.

## Small helper

If you want to automatically `cd` into the newly created project, a small helper function is needed in your shell's rc file, since scripts cannot alter your current working directory.

``` sh
echo 'boil() { command boil "$@" && while getopts 'n:' x; do case "$x" in; n) cd ~/build/"$OPTARG"; esac; done }' >> ~/.bashrc
```

You'll want to change `build` to whatever you put as your `default_dir`.

## Legal
Copyright (C) 2016 Daniel Gray <DanielFGray@gmail.com>

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.
