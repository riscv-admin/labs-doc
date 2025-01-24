
Setting Up GitLab Runner
************************

This page describes how users can host their own GitLab RISC-V runner for CI. This document assumes that you have a Linux operating system running on the RISC-V compute instance. 

Setup on GitLab UI
===================

1. Login to the GitLab web UI
2. Navigate to your GitLab project which you would like to configure with RISC-V GitLab CI runner
3. In the left menu, navigate to `Settings` and then `CI/CD`
4. Expand `Runners`
5. Uncheck `Instance runners`
6. Click on `New project runner`
7. Add `Tags`
8. Add `Runner description` and a `Maximum job timeout` value if desired
9. Click on `Create Runner`
10. On the next page select `Linux` as Platform
11. Copy the token and url from gitlab command (this will be used in configuring the compute instance)


Setup on RISC-V compute shell (Linux)
======================================

For hosting a GitLab RISC-V runner, you need to install GitLab runner package on your RISC-V compute instance. The GitLab runner `.deb` and standalone binary files are listed at this `link <https://cloud-v.co/risc-v-resources>`_

After downloading the gitlab runner standalone binary on a RISC-V compute instance, navigate to the directory where the binary file for RISC-V GitLab runner is present and use following command to register and run the runner. 

*Note: It is recommended to use separate terminal session (e.g. with tmux) for following commands so that you can safely detach the terminal without terminating the runner process. You can also start the `./gitlab-runner-linux-riscv64 run` as a background process, but then you will lose the log. There can be many solutions to this according to users' needs.*


.. code:: shell

   ./gitlab-runner-linux-riscv64 register --token <Your Token from GitLab here> --url https://gitlab.com # Get the token from GitLab
   # The terminal will prompt you for a name of the runner and an executor. The runner binary is tested with 'shell' executor
   ./gitlab-runner-linux-riscv64 run # This will start the gitlab runner process in the current terminal



