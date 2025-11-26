# Ruby LSP activation checklist

If the Ruby LSP extension fails to start or cannot find Ruby, walk through the steps below in order. Each fix builds on the previous one so you can stop as soon as the language server launches successfully.

1. **Confirm Ruby is installed and on the `PATH`.**  
   Run `ruby -v` in a regular shell. If you use a version manager (rbenv, rvm, asdf, mise) make sure the desired version exists (`rbenv install 3.3.0`, `asdf install ruby 3.3.0`, etc.) and is set for the workspace. Windows users relying on RubyInstaller should run `scripts/activate-ruby.ps1` so the toolchain is exported to the environment.
2. **Ensure your shell dotfiles load the version manager.**  
   VS Code's Ruby LSP host process does not automatically source `.zshrc`, `.bashrc`, etc. Unless `eval "$(rbenv init -)"`, `eval "$(asdf exec env)"`, `source ~/.rvm/scripts/rvm`, or `mise activate` is in a file that VS Code reads (login shell, `.profile`, or a shell hook launched by `code .`), the extension cannot discover Ruby. Double-check that the rc file VS Code picks up actually contains the initialization line.
3. **Launch VS Code from the configured shell.**  
   Opening VS Code via a desktop icon often uses `/bin/sh`, which bypasses your version manager. Always run `code .` from the terminal where Ruby already works, or explicitly set the default integrated terminal profile (Command Palette -> "Terminal: Select Default Profile") to the shell that bootstraps your environment. On Windows this repo already ships a **Ruby Dev Shell** profile that runs `scripts/activate-ruby.ps1`.
4. **Grant permissions on macOS.**  
   On Apple Silicon especially, VS Code sometimes needs Full Disk Access before it can read your Ruby installation. Go to **System Settings -> Privacy & Security -> Full Disk Access** and toggle **Visual Studio Code** on.
5. **Tell the extension which version manager you use.**  
   In VS Code settings search for `rubyLsp.rubyVersionManager` and pick the right entry (`"rbenv"`, `"asdf"`, `"mise"`, `"rvm"`, or `"none"` if Ruby is installed globally). This prevents the extension from guessing incorrectly.
6. **Provide an explicit Ruby path when no manager is used.**  
   Set `rubyLsp.customRubyCommand` (User or Workspace settings) to the Ruby executable. Examples: `C:\\Ruby34\\bin\\ruby.exe` on Windows or `/usr/local/bin/ruby` on macOS/Linux. The command must be executable without any wrapper scripts.
7. **Restart VS Code completely.**  
   "Reload Window" is not always enough. Quit VS Code, reopen it via `code .`, then watch the Ruby LSP output channel.
8. **Review the Ruby LSP output logs.**  
   Use **View -> Output** and select **Ruby LSP** in the dropdown. Errors here usually call out missing executables, failed shell commands, or permission denials. Address those messages directly and repeat this list as needed.

If the extension still refuses to start after all of the above, reinstall Ruby via your package manager (RubyInstaller on Windows, `brew`, `apt`, `asdf`, etc.) and ensure Bundler is available by running `gem install bundler`. Capture any log output when filing an issue so we can reproduce it.
