lava-tool Container
===================

Docker container to run lava-tool, which is only available as a debian package.

Usage
-----

    # Ensure proper ownership for lava-tool configuration
    mkdir -p ~/.local/share/lava-tool
    touch ~/.local/share/lava-tool/keyring.cfg
    chmod 600 ~/.local/share/lava-tool/keyring.cfg

    # Create alias that will mount in credentials as well as local path
    alias lava-tool="docker run --rm -i -v ~/.local/share/lava-tool:/root/.local/share/lava-tool -v \`pwd\`:/work danrue/lava-tool"

    # Run lava tool
    lava-tool -h

    # Set up a new configuration
    lava-tool auth-add https://<user>@validation.linaro.org/RPC2/
    lava-tool auth-config --endpoint-shortcut lkft https://<user>@lkft.validation.linaro.org/RPC2
    lava-tool auth-config --default-user https://<user>@lkft.validation.linaro.org/RPC2
    lava-tool auth-list

    # Submit a job
    lava-tool submit-job lkft x15.yaml


Caveats
-------

The container runs as root, so any directories mounted in using -v will be
accessed by the root user. The alias above mounts in a permissions file as well
as the current working directory when the tool is run.

See https://validation.linaro.org/static/docs/v2/lava-tool.html for additional
lava-tool documentation.
