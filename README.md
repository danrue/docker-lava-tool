lava-tool Container
===================

Docker container to run lava-tool, which is only available as a debian package.

Usage
-----

    mkdir -p ~/.local/share/lava-tool
    touch ~/.local/share/lava-tool/keyring.cfg
    chmod 600 ~/.local/share/lava-tool/keyring.cfg
    alias lava-tool="docker run --rm -i -v ~/.local/share/lava-tool:/root/.local/share/lava-tool -v \`pwd\`:/work danrue/lava-tool"
    lava-tool -h
    lava-tool auth-list

