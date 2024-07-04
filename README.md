<img src="./resources/header.png">

<br/>

```vim
set clipboard=unnamed            " Sets system synchronized clipboard register
set number                       " Enables line numbering
set relativenumber               " Enables relative line numbering. Along with `number` being set, produces hybrid line number mode
set cursorline                   " Highlights the current line
set ignorecase                   " Enables case-insensitive search
set smartcase                    " Enables smart case search, which is case-insensitive unless uppercase letters are used
set hlsearch                     " Enables highlighting of all matches for the search pattern

" Sets the leader key
let mapleader="\<Space>"

" Unbinds the Space key as it's used as the leader key
nnoremap <Space> <NOP>

" `Esc` - Remove search highlights
nnoremap <Esc> :nohl<CR>

" `<Alt> + z` - Toggle word wrap
noremap <A-z> :vsc Edit.ToggleWordWrap<CR>

" `<leader> + .` - Append a period to the end of the current line
" `<leader> + ,` - Append a comma to the end of the current line
" `<leader> + ;` - Append a semicolon to the end of the current line
" `<leader> + x` - Delete the last character of the current line
noremap <leader>. :norm A.<CR>
noremap <leader>, :s/\v\s*(,\s*)*$/,/<CR>:nohl<CR>
noremap <leader>; :s/\v\s*(;\s*)*$/;/<CR>:nohl<CR>
noremap <leader>x :s/.\{1}$//<CR>:nohl<CR>

" `<leader> + n(umber) + a(bsolute)` - Set absolute line numbers
" `<leader> + n(umber) + r(elative)` - Set relative line numbers
noremap <leader>na :set rnu!<CR>
noremap <leader>nr :set rnu<CR>

" `<leader> + w(indow) + p(in)` - Toggle the pin status of the document
" `<leader> + w(indows) + c(lose) + a(ll)` - Close all unpinned documents
noremap <leader>wp :vsc Window.PinTab<CR>
noremap <leader>wca :vsc Window.CloseAllButPinned<CR>

" `=` - Reformat code in the selected scope
" `=a` - Reformat code in the document
" noremap = :vsc ReSharper.ReSharper_ReformatCode<CR>
" ReSharper disabled:
noremap = :vsc Edit.FormatSelection<CR>
noremap =a :vsc Edit.FormatDocument<CR>

" `<Alt> + j` - Navigate to the next tab
" `<Alt> + k` - Navigate to the previous tab
" You might want to change these if you prefer horizontal tabs loayout
noremap <A-j> :vsc Window.NextTab<CR>
noremap <A-k> :vsc Window.PreviousTab<CR>
"noremap <A-l> :vsc Window.NextTab<CR>
"noremap <A-h> :vsc Window.PreviousTab<CR>

" `<Alt> + <Enter>` - Show action indicators and action list
" `<Ctrl> + <Space>` - Provide a completion list for partially typed words
noremap <A-CR> :vsc View.QuickActions<CR>
noremap <C-Space> :vsc Edit.CompleteWord<CR>

" `<leader> + r(emove) + s(ort)` - Remove and sort 'usings'
noremap <leader>rs :vsc Edit.RemoveAndSort<CR>

" `K` - Show quick information and/or parameter details tooltip
nnoremap K :vsc Edit.QuickInfo<CR>:vsc Edit.ParameterInfo<CR>:execute "normal! K"<CR>

" `]` - Navigate to the next member / type / tag
" `[` - Navigate to the previous member / type / tag
noremap ] :vsc Edit.NextMethod<CR>
noremap [ :vsc Edit.PreviousMethod<CR>

" `<Ctrl> + -` - Move backward through navigation history
" `<Ctrl> + =` - Move forward through navigation history
noremap <C>- :vsc View.NavigateBackward<CR>
noremap <C>= :vsc View.NavigateForward<CR>

" Improves navigation when wrapping
" by swapping `j` with `gj` and `k` with `gk`
nnoremap j gj
nnoremap gj j
nnoremap k gk
nnoremap gk k

" `<leader> + gd(eclaration)` - Navigate to a declaration of a symbol﻿
" `<leader> + gi(mplementation)` - Navigate to implementation of a type or a type member
" `<leader> + fa(sage)` - Find usages of any symbol from the solution and referenced assemblies﻿
noremap <leader>gd :vsc Edit.GoToDefinition<CR>
noremap <leader>gi :vsc Edit.GoToImplementation<CR>
noremap <leader>fa :vsc Edit.FindAllReferences<CR>

" `<leader> + f(ind) + f(iles)` - Search project items or locate a type﻿
" `<leader> + f(ind) + m(ember)` - Navigate to a file member or a textual occurrence
" `<leader> + f(ind) + w(ord)` - Navigate to a text occurrence in code and textual files﻿
noremap <leader>ff :vsc Edit.GoToType<CR>
noremap <leader>fm :vsc Edit.GoToMember<CR>
noremap <leader>fw :vsc Edit.GoToAll<CR>

" `<leader> + e(rror)` - Navigate forwards through all issues detected in the current file
" `<leader> + E(rror)` - Navigate backwards through all issues detected in the current file
noremap <leader>e :vsc View.NextError<CR>
noremap <leader>E :vsc View.PreviousError<CR>

" `<leader> + t(est) + r(un)` - Run unit tests from the current context
" `<leader> + t(est) + a(ll)` - Run all the tests in the solution
" `<leader> + t(est) + l(ast)` - Repeat a previous test run
" `<leader> + t(est) + f(ailed)` - Run only previously failed tests
" `<leader> + t(est) + c(over) + a(ll)` - Cover all tests in the solution
" `<leader> + t(est) + d(ebug)` - Start debugging the selected test
" `<leader> + t(set) + s(how) + s(essions)` - Show the unit test sessions window
" `<leader> + t(set) + s(how) + c(overage)` - Show the unit tests coverage results browser
noremap <leader>tr :vsc TestExplorer.RunSelectedTests<CR>
noremap <leader>ta :vsc TestExplorer.RunAllTests<CR>
noremap <leader>tl :vsc TestExplorer.RepeatLastRun<CR>
noremap <leader>tf :vsc TestExplorer.RunFailedTests<CR>
noremap <leader>td :vsc TestExplorer.DebugSelectedTests<CR>
noremap <leader>tss :vsc TestExplorer.ShowTestExplorer<CR>
noremap <leader>tsc :vsc View.CodeCoverageResults<CR>

" `<leader> + b + b(reakpoint)` - Toggle a breakpoint at the current line
" `<leader> + b(reakpoints) + d(isable)` - Disable all breakpoins
" `<leader> + b(reakpoints) + e(nable)` - Enable all breakpoints
" `<leader> + b(reakpoints) + r(emove)` - Remove all breakpoints
" `<leader> + b(reakpoints) + a(ll)` - Show the breakpoints list
noremap <leader>bb :vsc Debug.ToggleBreakpoint<CR>
noremap <leader>bd :vsc Debug.DisableAllBreakpoints<CR>
noremap <leader>be :vsc Debug.EnableAllBreakpoints<CR>
noremap <leader>br :vsc Debug.DeleteAllBreakpoints<CR>
noremap <leader>ba :vsc Debug.Breakpoints<CR>

" `<leader> + s(tart) + b(uild)` - Build the solution
" `<leader> + s(tart) + c(lean)` - Clean the solution
" `<leader> + s(tart) + b(uild)` + s(election) - Build the project that is currently selected
" `<leader> + s(tart) + c(lean)` + s(election) - Clean the project that is currently selected
" `<leader> + s(tart) + d(ebug)` - Start with debugging
" `<leader> + s(tart) + r(un)` - Run without debugging
" `<leader> + s(tarted) + b(uild) + c(ancel)` - Cancel the build
" `<leader> + s(tarted) + d(ebug) + c(ancel)` - Stop debugging
noremap <leader>sb :vsc Build.BuildSolution<CR>
noremap <leader>sc :vsc Build.CleanSolution<CR>
noremap <leader>sbs :vsc Build.BuildSelection<CR>
noremap <leader>scs :vsc Build.CleanSelection<CR>
noremap <leader>sd :vsc Debug.Start<CR>
noremap <leader>sr :vsc Debug.StartWithoutDebugging<CR>
noremap <leader>sbc :vsc Build.Cancel<CR>
noremap <leader>sdc :vsc Debug.StopDebugging<CR>

" `<leader> + q(ick) + w(atch)` - Show the QuickWatch dialog box
" `<Ctrl> + <Left>` - Move execution pointer to the selected statement
" `<Ctrl> + <Right>` - Step over
" `<Ctrl> + <Down>` - Step into
" `<Ctrl> + <Up>` - Step out
nnoremap <Leader>qw :vsc Debug.QuickWatch<CR>
nnoremap <C-Left> :vsc Debug.SetNextStatement<CR>
nnoremap <C-Right> :vsc Debug.StepOver<CR>
nnoremap <C-Down> :vsc Debug.StepInto<CR>
nnoremap <C-Up> :vsc Debug.StepOut<CR>

" `<leader> + /` - Comment/uncomment the current line
" `<leader> + kc` - Comment the selection
" `<leader> + ku` - Uncomment the selection
" `<leader> + kw` - Comment the selection with /* */
noremap <leader>/ :vsc Edit.ToggleLineComment<CR>
noremap <leader>kc :vsc Edit.CommentSelection<CR>
noremap <leader>ku :vsc Edit.UncommentSelection<CR>
vnoremap <leader>kw di/*<Esc>pa*/<Esc>
nnoremap <leader>kw diwi/*<Esc>pa*/<Esc>

" `<leader>mx` - Expand all regions 
" `<leader>cx` - Colapse all regions
" `<leader>cc` - Colapse current region
nnoremap <leader>mx :vsc Edit.ExpandAllOutlining<CR>
nnoremap <leader>cx :vsc Edit.CollapseAllOutlining<CR>
nnoremap <leader>cc :vsc Edit.CollapseCurrentRegion<CR>

" `<leader> + sa` - Save all
nnoremap <leader>sa :vsc File.SaveAll<CR>

" `<leader> + rr` - Refactor Rename
" `<leader> + rm` - Refactor Method
" `<leader> + rs` - Surround with
nnoremap <leader>rr :vsc Refactor.Rename<CR>
vnoremap <leader>rm :vsc Refactor.ExtractMethod<CR>
vnoremap <leader>rs :vsc Edit.SurroundWith<CR>

" `<leader> + qk` - Customize Keyboard
map <leader>qk :vsc Tools.CustomizeKeyboard<CR>

" `zl` - Shout out config file
nnoremap zl :so ~/.vsvimrc<CR>

" `<leader> + d` - Duplicate Selection
noremap <leader>d :vsc Edit.Duplicate<CR>

" `<leader> + <leader>` - Start vim search
nnoremap <leader><leader> /

" `o` - Add line below with normal mode
" `O` - Add line abowe with normal mode
" `<leader> + o` - Add line below with insert mode
" `<leader> + O` - Add line abowe with insert mode
" `<leader> + Enter` - Split the line
nnoremap o o<Esc>
nnoremap O O<Esc>
nnoremap <leader>o o
nnoremap <leader>O O
nnoremap <leader><CR> a<CR><Esc>
```