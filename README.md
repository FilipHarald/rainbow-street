# rainbow-street

## Installation
### Build from source
Requires [Rust](https://www.rust-lang.org/tools/install).

```bash
git clone git@github.com:FilipHarald/rainbow-street.git
cd rainbow-street
cargo build --release
cp ./target/release/rainbow-street $HOME/bin/rstrt
```

## Usage
### When listing files
```bash
find ~/* | rstrt
```

### Use in prompt
Use this in your `.bashrc`.
```bash
promptFunc() {
  if [[ -x $(realpath "$HOME/bin/rstrt") ]]
  then
    WD=`pwd | $HOME/bin/rstrt`
    COLORIZED_DIR=`echo "${WD}" | awk -F/ '{print $NF}'`
    PS1="\`echo -e \"\[\a\]\[\033[01;32m\]\h\[\033[01;34m\] ${COLORIZED_DIR} \$ \"\`"
  else
    PS1='\[\a\]\[\033[01;32m\]\h\[\033[01;34m\] \W \$ \[\033[00m\]'
  fi
}
PROMPT_COMMAND="promptFunc"
```

