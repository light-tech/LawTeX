LawTeX - Best LaTeX Editor
==========================

The best tool to write TeX/LaTeX document & the best friend of academics

[Get it on Microsoft Store](https://www.microsoft.com/en-us/p/lawtex/9nblggh16jqz)

Our Unique Features - Fast Automatic Recompile
----------------------------------------------

LawTeX was developed out of the _awful experience_ of writing LaTeX using existing editors such as TeX Maker, WinEdt, TeXworks even decades after Knuth's invention: 
 1. _the time taken from making some changes to actually see the changes in the PDF is just too long_.
 2. Not only that, one _has to_ press a key combination such as `F9` on WinEdt or `Ctrl+T` on TeXworks to start the compilation.
Having to do so repeatedly hinders a mathematician's productivity significantly when he/she was doing mathematics; for example, typical tasks such as manipulating equations, computing integrals, etc. requires making many changes that are best with immediate visual feedback so that the calculations are ensured to be correct.

Thus, we decided to build a new LaTeX editor with two main goals:
 1. __Automatic recompilation of TeX file__ as you pause typing, bringing TeX closer to a WYSIWYG experience
 2. __Reduce compilation time to allow fast visual feedback__

The key task is #2.
Existing editors could not accomplish that due to the fact that compilation takes prohibitively long for repeated recompilation.
This is to be expected for after all, TeX was originally designed to generate documents for publishing, not for development of the document itself i.e. once you have all the material ready (hand-calculated formulas), writing should be a breeze.

With our accomplishment in LawTeX, recompilation can start as soon as 1 second (or even lower, but we do not support that for now) after you stop typing.
Thank to the two unique features, the original author already produced many scientific documents with __fairly few calculation mistakes__, much fewer than should he had done the calculation by hand: Imagine copy and paste a formula, simplify it piece-by-piece, see the modification instantly rendered and verify the changes. It is significantly better and less error-prone than copying by hands.

With everything said, __LawTeX does not aim to replace other TeX distributions__!
It works best for academic papers but not fancy TeX features: to write the document, not publishing them (that is, the opposite of TeX!).
For publication, traditional pdfTeX should be preferred in order to generate high qualify printable output.

Along the way, we also improve other aspect of TeX such as installation.

Features
--------

LawTeX provides an integrated environment to compose, compile LaTeX documents to DVI files, and view the DVI result.
 1. Like MiKTeX a.k.a. the standard TeX distribution for Windows PC, LawTeX can __identify missing packages and offer to download__ missing ones. It supports many major engine-independent macro packages such as xypic, amsthm, babel, algorithmics, preprint, etc. on CTAN while packages for modern fonts such as true type, open type fonts or those depending on other engines (e.g. moderncv requires pdfTeX) are not available.
 2. Our LaTeX editor features a __highly optimized editor__ with __code completion__, implemented in C++ using Direct X (the native graphic engines for Windows featured in most video games). It supports typical editing tools such as Undo/Redo, Cut/Copy/Paste, Selection, Go to line, Find/Replace/Replace All using regular expression, Line numbering, etc.
 3. Exceptional performance: Unlike MiKTeX, the __memory footprint of this app is minute__. The app is roughly 2MB in download size, roughly 10MB when installed compared to 300-450MB basic MiKTeX installation, discounting the packages. In addition, the document and temporary files are kept entirely in RAM so it not only makes compilation faster but also avoids wasting precious write cycles of your SSD and SD card. The memory (RAM) usage is smaller than typical editor such as TeX Maker.
 4. <del>TeX on the go: available across your Windows 10 PC, tablet and Windows 10 mobile phones. The user interface is designed to make it easy to work on all these devices. For example: keyboard shortcuts on PC/tablet with physical keyboard; on-screen context menu to perform typical editing actions like Cut/Copy/Paste and text selection.</del>
 5. Also support BibTeX This app registers .tex file extension so you can pick it as default app to open your LaTeX documents.

USAGE NOTES
 * Keyboard shortcut: - Ctrl+X, Ctrl+C, Ctrl+V for cut/copy/paste - Ctrl+A to select the whole text - Ctrl+Z and Ctrl+Y for undo/redo - Ctrl+T to compile document - Ctrl+S to save document - Ctrl+F to open Find/replace panel, Ctrl+G to open Go to line panel
 * Should save frequently on 512MB RAM phones. The app might crash or hang especially when deleting text or inserting new lines. We believed that most bugs are bashed; but bugs due to concurrency are very hard to create and are device dependent.
 * TIP: If you have a document produced using other editors but does not work on LawTeX, try commenting the whole document, uncomment it piece by piece to see what works and what does not.
 * TIP: Try our samples at [https://github.com/light-tech/LawTeXSamples](https://github.com/light-tech/LawTeXSamples)

HISTORY
----------

Version 2.7.0.0
 * Completely rewritten the app in C++/WinRT
    - Smaller app size
    - Better performance
    - Battery efficiency: Old LawTeX uses the Direct X game template which redraws the editor 10 times per second while the new version redraws only when necessary such as scrolling/typing
    - Fixes many long standing crash due to concurrency programming thank to much better coding pattern with coroutine
    - Many internal system implementation improvements
 * UI: Switch to a familiar desktop menu bar
    - More screen estate
    - Logical grouping of actions
    - Inform users of the keyboard shortcuts
 * UX: Enhance error reporting by showing a message dialog
    - When the app does not have file system permission to compile
    - If downloading package when there's no Internet connection
 * UX: Enhance user friendliness with welcome dialog

Version 2.6.4.0
 * Hot fix for crash when putting DVI in a separate window due to some non-thread-safe UI optimization previously performed

Version 2.6.3.0
 * Fix bug regarding missing fonts, unless manually install `metafont.lfs`
    - Doesn't affect existing users since they probably already have `metafont.lfs`
    - This is due to failure to keep track and notify user to download the required package.
 * Small efficiency enhancement
    - Skip font processing once a missing package is encountered; redo after download

Version 2.6.2.0
 * Add a new setting regarding DVI resolution i.e. more crispy fonts
   - Note: 300 dpi seems to work best for HD screen 1920 x 1080; probably 600 dpi is good for 4K

Version 2.6.1.0
 * More standard conformance code
 * Incorporate pdfstrcmp to ELTeX engine to (sort of) support LaTeX3 (only work with our old version of LaTeX3 from 2015, not the latest version)
 * Fix inefficient line number rendering
 * Fix crash on start-up if automatic compilation is enabled
 * Temporarily disable compilation of the ``Untitled'' document
 * Fix long-existing crash when Find/Replace after switching document

Version 2.6.0.0
 * Automatically load additional \input files and resources (SVG files) from file system using broadFileSystemAccess permission
    - SVG and \input support continues to work even if you do not grant LawTeX broadFileSystemAccess; but in that case, you must open each of those input files manually.
 * Enhance source resolution mechanism: LawTeX now looks for \input files in in the following order
   (i)   editor;
   (ii)  current working directory (i.e. folder containing the main file being compiled);
   (iii) distributed packages.
    - In this release, we do not support general relative paths (those involved . and ..) yet.
    - Also, due to inherent inefficiency of the UWP (Microsoft's distrustfulness of developers ability), each file look-up in working directory is EXPENSIVE (in particular, need to be handled in a new thread which is unnecessarily since the whole compilation is already in a background task). You will notice the first compilation is much slower compared to previous version. Therefore, we only do that for the following 4 file types *.tex, *.ltx, *.bib and *.svg.
 * Internal system efficiency improvement: Editor content is communicated directly to the compiler.
    - No longer need to do a dummy compile of (TeX, BibTeX, SVG) files opened.
    - No more intermediate memory allocation.
 * Settings framework enhancement
 * Fix various memory leak

Version 2.5.9.0
 * Lift memory limit to support beamer
 * Programming memory model improvements in editor
 * Eliminate most of C++ standard classes using memory efficient in-house template classes (tree, list, array, map, string)

Version 2.5.1.0 - 2.5.3.0
 * Minor bug fixes and safety improvements
 * Switch to e-TeX engine for \ifdefined primitive
 * Enhance internal system efficiency

Version 2.5.0.0
 * BibTeX support

Version 2.4.1.0
 * Now use SVG  support in Direct X SDK available in Creator Update.
 * Since this update is generally out of reach for most Windows 10 phones, we will no longer build version for ARM.

Version 2.4.0.0
 * UI revamp with no xaml approach; extract Settings to a dialog to offload the UI
 * No longer auto show up the log view; click button to open
 * Fix crash when inserting suggestion due to failure to consider Windows line ending \r\n
 * Enhance suggestions database with more than 2000 suggestions; suggestions bundled in code instead of parsing from file for performance
 * Fix double paste when attempt to paste to the Search/Replace boxes
 * Add button to launch app website for usage instructions and tips

Version 2.3.3.0
 * Support showing DVI viewer in a separate window or force screen splitting  (select in Settings; app restart required)

Version 2.2.0.0 - 2.3.2.0
 * Major improvements in editor thank to development of our DevMax app

Version 2.1.4.0
 * Support for external file resources (can do \input and \include)
    - Open additional source files (such as *.cls, *.tex) via the Load menu, Compile the [included] file and then Compile the main file
 * Support include graphics such as SVG (this feature might be scrapped due to low usage potential and lack of support by TeX community; originally intended for doing presentation right from LawTeX without having to compile to PDF)
     - Direct inclusion by adding \special{<svg>YOUR SVG CODE}
     - Reference inclusion by adding \special{includesvg NAME_OF_SVG_FILE} (must open SVG via the Load menu, Compile the SVG before compiling the main file to view the DVI)
 * Fix dangling pointer bug (cause crash)
 * Minor UI fixes

Version 2.1.3.0
 * Improvements in the internal system to support context sensitive highlighting such as block/multiline comment with \iffalse ... \fi. The editor now render Windows line ending properly. Add setting to highlight the current line.

Version 2.1.2.0
 * Fix UTF-8 encoding handling; \usepackage[utf-8]{inputenc} should now work properly
 * Notify user to download necessary packages for missing fonts as well
 * Fix memory leak and other minor bugs

Version 2.1.1.0
 * Switch to new package server. Current app MUST update to install new packages: Starting from Aug, 31st 2016, the existing server will not work.

Version 2.1.0.0
 * Many bug fixes (such as weird incomplete copy/paste and French keyboard issue)
 * Option for desktop-like selection (click and move mouse to select a block of text) and perform Home/End visually
 * Options to control DVI extra margin
 * Option not to prompt when missing package is encountered
 * Handle DVI color special; can now render *beamer* slide and syntax highlight code *listings* nicely (NB: some beamer features such as round boxes relies  heavily on PostScript which cannot be handled; hopefully the beamer developer can switch to SVG)
 * Support (simplistic/English-US only) spell checking (turn on in Settings)
 * Remove most embedded basic packages (latex, amsmath, ... should now be downloaded from our server instead) to reduce app size
 * Remove 1MB of characters text limit; more efficient memory usage
 * Use the file's name in the compiler instead of generic "document.tex"; MUST NOT name file with weird characters and also avoid spaces

Version 2.0.9.0
 * Fix minor annoyances in file name label; Make interaction independent between documents so that scrolling on one document do not scroll other; Enhance internal system with lazy package loading (packages are loaded as needed instead of all at once at start-up; should enhance the app experience especially on phone); Register DVI file (can now open DVI in file explorer for viewing); Add option to save generated fonts to local folder (we recommend to enable this option on phone to enhance DVI viewing experience)

Version 2.0.8.0
 * Integrate with system input method (can now swipe through letters to input text on Windows 10 Mobile onscreen keyboard or use hand writing input panel on PC); Add natural touchscreen scrolling gesture; New app logo to integrate well with the Windows 10 Mobile tile start screen; Export DVI; Fix bug regarding keyboard popping up when it shouldn't be (for e.g. after pressing compile button or close the log); Fix crash when pasting without copy/cut; Fix other bugs

Version 2.0.7.0
 * Support multiple documents; add option to auto-compile and auto-save periodically; First release for Windows 10 Mobile with customized user interface, back pressed handling, ...

Version 2.0.6.0
 * Support non-US-English keyboard; implement literal (non-regex) search; fix editor font settings

Version 2.0.5.0
 * Fix insertion of pipe | character, minor UI revamp such as displaying file name, and many other bug fixes such as crashing after resuming from lock screen and "Find next" not jumping to the location where the text is found

Version 2.0.4.0
 * First universal app release for Windows 10