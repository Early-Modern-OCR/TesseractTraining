<h1>TesseractTraining</h1>

<p>Training files produced for and by the Tesseract OCR engine for work on the Early Modern OCR Project (eMOP)</p>


<h2>Dictionaries:</h2>
<ul>
<li><b>Raw</b>: This folder contains raw, word list files gathered from a variety of sources</li>
<ul>
The following files were collected from various sources by Ted Underwood and pass on to us. Most are not simple word lists and contain words counts, alternate spellings, etc.
<li><i>addToDictionary.txt</i></li>
<li><i>gazetteer.txt</i></li>
<li><i>maindict.txt</i></li>
<li><i>romannumerals.txt</i></li>
<li><i>SyncopeRules.txt</i></li>
<li><i>VariantSpellings.txt</i></li>
</ul>
</ul>
<br />

<ul>
The following files were generated by eMOP using an R program to count word frequecy from the Text Creation Partnership (TCP) corpus of hand-transcribed texts.
<li><i>ecco-TCP-word-freq.txt</i></li>
<li><i>eebo-TCP-word-freq.txt</i></li>
</ul>
<br />

<ul>
The following file was gathered from the VARD tool of early modern variant spelling.
<li><i>variants.txt</i></li>
</ul>

<ul>
The following file was sent to us by Martin Muller who extracted this file of alternate spellings using MorphAdorner. It is broken up by time periods.
<li><i>emopspellings.txt</i></li>
</ul>

<li><b>Cleaned</b>: This folder contains cleaned up versions of the Raw files, with just the words left.</li>

<li><b>Combos</b>: This folder contains alphabetically sorted word lists that are combinations of the cleaned lists with all duplicates removed. Files with a suffix of "-CSU" have been cleaned, sorted, and all entries are unique (no duplicates). Files that are underlined and bold, are what we have used in eMOP as the basis for our freq-dawg and word-dawg word lists when training Tesseract to run on the eMOP data set of 45 million page images.</li>
<ul>
<li><i>FullDict-184k.txt</i>: A combination of all cleaned files received from Ted Underwood (addToDictionary, gazetteer, maindict, romannumerals, SyncopeRules, and VariantSpellings).</li>
<li><i>FullDict-wVariants-CSU</i>: A combination of FullDict-184k.txt and the cleaned variants.txt culled from VARD (variants-CSU.txt). Cleaned, sorted, and unique.</li>
<li><i>TCP-words-btwn100-499.txt</i>, <i>TCP-words-gt100.txt</i>, <i>TCP-words-gt500.txt</i>: Are combinations of the word lists we compiled from the TCP for both EEBO and ECCO documents, and split into various word-frequency ranges.</li>
<li><i>TCP-words-GT-100-wVariants-CSU.txt</i>: A combination of EEBO and ECCO TCP words, with variants-CSU.txt. Cleaned, sorted and unique.</li>
</ul>

</ul>

<p>After much testing with Tesseract of all these various files, combination files, and other combinations, we finally decided on using:
<ul>
<li><b><i>FullDict-wVariants-CSU.txt</i></b> as our main word list (<b>word-dawg</b>), and </li>
<li><b><i>TCP-words-gt500.txt</i></b> as our frequently used word list (<b>freq-dawg</b>.</li>
</ul>
</p>

<br/><br/>

<h2>FontTraining:</h2>
<ul>
<li><b>forEMOP</b>: This folder contains .traineddata, .box, and .tif files used to create the font training for Tesseract on the eMOP project. There are also sample images of each typeface used to create the training as binarized .tif images.</li>
<li><b>notUsed</b>: This folder contains .traineddata, .box, and .tif files used to create the font training for Tesseract, which, after extensive testing, we did not end up using on the eMOP project for various reasons. There are also sample images of each typeface used to create the training as binarized .tif images.</li>
<li><b>combos</b>: This folder contains .traineddata files of every Blackletter typeface we created training for (BL5-All-D2.traineddata) and every Roman &amp; Italic typeface we created training for (RI5-All-D2.traineddata). Both files were created using training from the <i>forEMOP</i> and <i>notUsed</i> folders.</li>

<p>The <i>forEMOP</i> and <i>notUsed</i> folders both contain multiple folders cover typefaces created by/for specific individuals. The name convention for the folders is<br/>
<blockquote>&lt;name&gt;-&lt;font type&gt;-&lt;year(s) of creation&gt;</blockquote>
where
<ul>
<li><b>&lt;font type&gt;</b> can be any combination of 
<ul>
<li><b>R</b>: Roman</li>
<li><b>I</b>: Italic</li>
<li><b>B</b>: Blackletter</li>
</ul></li>
<li><b>&lt;year(s) of creation&gt;</b>is one or more years, separated by a '-'.</li>
</ul></p>

<p>Each of these folders contains
<ul>
<li>A '.traineddata' file, which can be placed in any local tessdata file and used to OCR page images using that typeface or a similar one.</li>
<li>A '.tar.gz' file, which contains the box/tif file pairs we created with Franken+ (https://github.com/Early-Modern-OCR/FrankenPlus) for each of these typefaces. For typefaces with multiple styles (roman, italic, blackletter, alternate roman, etc.), and/or multitple styles the differences can be seen in the names of the box/tif file pairs.</li>
<li>A 'sample/' folder of binarized tifs of some of the page images used to create the training for that typeface.</li>
</ul></p>

<p>Inside the <i>forEMOP</i> folder is a 'combos/' folder containing <b>SC8b-R7-D2b.traineddata</b>, which is the training file we used to OCR the eMOP corpus. It contains:
<ul>
<li><b>Typeface training</b> for all of the typefaces listed in the 'forEMOP' folder.</li>
<li><b>Dictionary files</b>created using https://github.com/Early-Modern-OCR/TesseractTraining/blob/master/Dictionaries/Combos/FullDict-184k.txt to generate the word-dawg file and https://github.com/Early-Modern-OCR/TesseractTraining/blob/master/Dictionaries/Combos/TCP-words-gt500.txt to generate freq-dawg.</li>
</ul></p>

</ul>

<br/><br/>

<h2>MiscFiles:</h2>
<p>This folder contains two other files that we used to create the Tesseract typeface training in this repo:
<ul>
<li><b>F+TrainingText-4.txt</b>: This is a text file used with <a href="https://github.com/Early-Modern-OCR/FrankenPlus">Franken+</a> to create tif/box pair files for a typeface. Once Franken+ has been used to identify the glyphs to be used to create training for Tesseract, this text file is used to create a set of "Franken-tifs" that are this text "printed" with the glyphs identified in Franken+. The corresponding box files are then created from those tifs and are used to create the training (.tr files) for Tesseract. This text file contains mulitple uses of ever character glyph that we identified in our work including special characters and ligatures. Most of these are identified and given Unicode values in the <a href="https://github.com/Early-Modern-OCR/FrankenPlus">MUFI set</a>.</li>
<li><b>emop.unicharambigs</b>: This is a file used when creating the final .traineddata file of Tesseract training for a typeface or set of typefaces. It is used by eMOPM to convert all special characters and ligatures into standard, modern equivalent characters (i.e. those found on a keyboard).</li>
</ul></p>
