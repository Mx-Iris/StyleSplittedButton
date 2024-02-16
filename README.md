# Why this Library was created

The NSButton is undeniably the most intricate component in AppKit. It encompasses a wide range of styles and button types, which can be confusing due to inconsistent naming conventions across header files, Xib, and HIG. In macOS Sonoma, Apple has even introduced further renaming complexities. This exacerbates the already convoluted definition, making it more challenging to comprehend. 

The Library does not enhance any functionality but rather extracts a style into a separate subclass with an unalterable bezelStyle and buttonType. It only provides the buttonType that aligns with the current style, while some names found in Xib and HIG are offered as Typealias. The actual class name is BezelStyle or ButtonType (renamed according to the latest Sonoma nomenclature). 

If you struggle to grasp how each button should be utilized and where it should appear, I recommend reading this article (https://mackuba.eu/2014/10/06/a-guide-to-nsbutton-styles/) before exploring this repository.
