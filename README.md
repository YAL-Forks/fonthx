# fonthx: Simple TrueType Generation for Haxe

* A very basic font generation library (currently TrueType only) written in [Haxe](https://haxe.org)
* The core of the font generation module used by [FontStruct](https://fontstruct.com) 
* Aimed at Haxe (or other) developers who wish to create font generation tools
* Should work with nodejs, js, cpp, c# and java targets. WASM too

## Installation

1. Install Haxe: https://haxe.org/download/       
    
1. Install Haxe dependencies

        haxelib install haxelib.json
        
1. To compile for node, you will need to have nodejs installed. To compile for java, you will need to have java installed. Other requirements listed below.       
    
## Try it for node

    haxe build/examples/pixelfonter/pixelfonter-node.hxml
    
This will build the pixelfonter example, which will create a TrueType font from a PNG image.

## Try the same thing for Java

    haxe build/examples/pixelfonter/pixelfonter-java.hxml
    
## Try the same thing for native C++

    haxe build/examples/pixelfonter/pixelfonter-cpp.hxml    
    
## And C# !?!

    haxe build/examples/pixelfonter/pixelfonter-cs.hxml    

– In order to use this example on OSX or Linux you will need to install mono, e.g. via brew install mono

## And in the browser with a simple GUI

    haxe build/examples/pixelfonter/pixelfonter-js.hxml    

– In order to view this example, you will need to point a web server at dist/examples/pixelfonter/js/index.html

## And even with WASM!
    
    HXCWD=`pwd` haxe build/examples/pixelfonter/pixelfonter-wasm.hxml     

– You will need to setup emscripten in order to compile this one. You will also need to point a web server at dist/examples/pixelfonter/wasm/index.html. The easiest way is with emrun e.g.

    emrun --no_emrun_detect --browser chrome dist/examples/pixelfonter/wasm/PixelFonterBrowserApp-debug.html
    
(May well take a while to initialise)    
    
## Developing and Testing

Set up the dev tools (gulp):

    npm install
    
Run specs:

    gulp specs
    
Or, develop and run specs:

    gulp specs-watch
    
Develop using the pixelfonter example app (node target):     
    
    gulp pixelfonter-watch
    
Show all the available gulp tasks:

    gulp --tasks
    
## Build a font generation tool

Look at the Pixelfonter example for guidance, in particular fonthx.examples.pixelfonter.PixelFonter.

You need to:

1. create a font class implementing fonthx/model/IFont (optionally extending AbstractFont)
1. create a glyph class implementing fonthx/model/IContourGlyph (optionally extending AbstractContourGlyph)
1. instantiate your font class, add some glyphs to it, then
1. get your TrueType bytes using fonthx.formats.tt.TrueTypeBuilder

    