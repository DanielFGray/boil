# Boiler

Custom boilerplates

## Usage

```
boil <NAME> [TEMPLATES...]
```

## Example Configuration

Imagine you want to create a React.js project, but every time you 

``` sh
cd ~/.config/boiler
echo "default_dir	$USER/build" > conf
echo 'git init' > all
mkdir js && cd js
echo 'npm init -y' > all
echo 'npm i -S react react-dom' > react
```

`boil newreact js/react` would then execute:

``` sh
mkdir "$USER/build/newreact"
git init
npm init -y
npm i -S react react-dom
```

## Small helper

If you want to automatically `cd` into the newly created project, a small helper function is needed in your shell's rc file, since scripts cannot alter your current working directory.

``` sh
echo 'boil() { command boil "$@" && cd ~/build/"$1"; }' >> ~/.bashrc
```
