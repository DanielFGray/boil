# Boiler

Generic custom boilerplates

## Usage

```
boil <NAME> [TEMPLATES...]
```

## Example Configuration

Imagine you want to create a React.js project, but every time you do this, you have a series of commands you execute:

``` sh
mkdir ~/build/newreact    # this happens for every project
git init                  # this happens for every project
npm init -y               # this happens for every javascript project
npm i -S react react-dom  # this happens for every react project
```

`boil newreact js/react` can do this for you with the following configuration:

``` sh
cd ~/.config/boiler
echo 'default_dir	$USER/build' > conf        # where to boil every new project
echo 'git init' > all                        # this happens for every project

mkdir js
echo 'npm init -y' > js/all                  # this happens for every javascript project
echo 'npm i -S react react-dom' > js/react   # this happens for every react project
```

## Small helper

If you want to automatically `cd` into the newly created project, a small helper function is needed in your shell's rc file, since scripts cannot alter your current working directory.

``` sh
echo 'boil() { command boil "$@" && cd ~/build/"$1"; }' >> ~/.bashrc
```
