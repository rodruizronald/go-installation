# Install and manage multiple Golang versions

Only for Unix base systems such as **Linux** and **macOS**.

## 1. Download Go binary

See a complete list of releases [here](https://go.dev/dl/). Pick the version you would like to install. For this guide, I will install version `1.21.4`. Choose the filename with extension `tar.gz` that suits the architecture of your machine. In my case, I am using a Mac with an ARM processor so I will download the filename `go1.21.4.darwin-arm64.tar.gz`. To download run:

```bash
curl -OL https://golang.org/dl/go1.21.4.darwin-arm64.tar.gz
```

## 2. Create binary directory

```bash
sudo mkdir -p /usr/local/go/v1.21.4
```

## 3. Extract binaries

```bash
sudo tar -xvf go1.21.4.darwin-arm64.tar.gz -C /usr/local/go/v1.21.4 --strip-components=1
```

## 4. Setup workspace

Go uses the `$GOPATH`  to indicate a single workspace for third-party Go tools installed via `go install`. By default this workspace is located in `~/go` with the following subdirectories:

```bash
go
├── bin
└── src
```

- src: Source code for third-party Go tools.
- bin: Compiled binaries.

Create the directories

```bash
mkdir -p ~/go/v1.21.4/bin
mkdir -p ~/go/v1.21.4/src
```

## 5. Add paths

It's a good practice to explicitly define the `$GOPATH` and to put the `$GOPATH/bin` directory in the executable path. This makes crystal clear where the Go workspace is located and easier to run third-party tools installed via `go install`.  

Add the following lines in your `~/.zprofile` for macOS user or `~/.bash_profile` for linux users.

``` bash
# Golang environment setup
#
# Source code of the golang version used by the system
export GOROOT=/usr/local/go/v1.21.4
export PATH=$PATH:$GOROOT/bin
#
# Workspace for third-party Go tools installed via go install
export GOPATH=$HOME/go/v1.21.4
export PATH=$PATH:$GOPATH/bin
```

Apply the changes in the system

```bash
source $HOME/.profile
```

## 5. Verify installation

```bash
go version
```

If everything is set up correctly, you should see something like this printed: `go version go1.18.2 linux/amd64`

## 6. Update version

If you would like to install a new version, then just start from step 1 and in step 5 just change the directory from `v1.21.4` to the new one.
