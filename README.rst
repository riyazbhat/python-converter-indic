======================
python-converter-indic
======================

A python library for implementing UTF to WX converter and vice-versa for Indian languages.

Installation
============

Dependencies
~~~~~~~~~~~~

::

    None

Download
~~~~~~~~

Download **python-converter-indic**  from `github`_.

.. _`github`: https://github.com/irshadbhat/python-converter-indic

Install
~~~~~~~

::

    tar xvfz python-converter-indic.tar.gz
    cd python-converter-indic
    sudo python setup.py install

Example
~~~~~~~

1. **utf to wx (plain text):**

::

    >>> from converter_indic.ilp import wxConvert
    >>> 
    >>> # class wxConvert(order="utf2wx", format_="text", lang="hin")
    ... # Parameters: order:str, (default="utf2wx"), source2target encoding [wx2utf|utf2wx]
    ... #	      format_:str, (default="text"), output format [text|ssf|conll|bio|tnt]
    ... #	      lang:str, (default="hin"), language parameter [hin|tel|...] (3 letter ISO-639 code)

    >>> con = wxConvert(order='utf2wx')  # here default language is hindi and default format is text
    >>> 
    >>> hin = """
    ... 1   देश के कई हिस्सों में सूखे के आसार उत्पन्न हो गए हैं
    ... 2   अब तक मौसम विभाग सामान्य बारिश होने की अपनी भविष्यवाणी पर अड़ा हुआ था लेकिन अब यह दावा पूरी तरह से खारिज हो गया है
    ... 3   देश भर में अब तक हुई बारिश औसत से छह फीसदी कम है जबकि विभाग का दावा था कि इसमें ५ फीसदी से ज्यादा कमी नहीं होगी
    ... 4   इसके चलते उत्तर प्रदेश पंजाब हरियाणा राजस्थान बिहार झारखंड आदि राज्य लगभग सूखे की चपेट में हैं
    ... 5   लेकिन तकनीकी कारणों से इन्हें अभी सूखाग्रस्त घोषित नहीं किया गया है
    ... """
    >>>
    >>> print con.convert(hin)
    
    1   xeSa ke kaI hissoM meM sUKe ke AsAra uwpanna ho gae hEM
    2   aba waka mOsama viBAga sAmAnya bAriSa hone kI apanI BaviRyavANI para adZA huA WA lekina aba yaha xAvA pUrI waraha se KArija ho gayA hE
    3   xeSa Bara meM aba waka huI bAriSa Osawa se Caha PIsaxI kama hE jabaki viBAga kA xAvA WA ki isameM 5 PIsaxI se jyAxA kamI nahIM hogI
    4   isake calawe uwwara praxeSa paMjAba hariyANA rAjasWAna bihAra JAraKaMda Axi rAjya lagaBaga sUKe kI capeta meM hEM
    5   lekina wakanIkI kAraNoM se inheM aBI sUKAgraswa GoRiwa nahIM kiyA gayA hE
    
    >>> tel = """
    ... 1   తమ 35 ఏళ్ల పెళ్లి సందర్భంలోనూ - అనుక్షణం శత్రువులకు మల్లే కాట్లాడుకోవటం బంటీకి నచ్చదు.
    ... 2   2007లో అజ్మీర్‌లోని ఖాజా మొయినుద్దీన్ చిష్తీ దర్గాలో జరిగిన పేలుడులో ముగ్గురు చనిపోగా, మరో 15 మంది గాయపడిన విషయం తెలిసిందే.
    ... 3   గణితం లాంటి విషయం గురించి బ్లాగులు, వీకేల ద్వారా చర్చలు జరగవచ్చునని అందరికీ అర్థమయింది.
    ... 4   ఇలా ఇంత పోటీలో, యాంటీ బ్రిటిష్ వాతావరణంలోను 155 నిముషాల నిడివిగల ‘హామ్లెట్’ నిలిచి గెలిచిందంటే అది దాని చక్కదనానికి నిదర్శనమే!
    ... 5   అవకాశం వచ్చిన వారికి ఎక్స్‌పోజర్‌కూడా వస్తుంది.
    ... """
    >>> 
    >>> con = wxConvert(order='utf2wx', lang='tel')
    >>>
    >>> print con.convert(tel)
    
    1   wama 35 elYla peVlYli saMxarBaMlonU - anukRaNaM Sawruvulaku malle kAtlAdukovataM baMtIki naccaxu.
    2   2007lo ajmIr‌loni KAjA moVyinuxxIn ciRwI xargAlo jarigina peludulo mugguru canipogA, maro 15 maMxi gAyapadina viRayaM weVlisiMxe.
    3   gaNiwaM lAMti viRayaM guriMci blAgulu, vIkela xvArA carcalu jaragavaccunani aMxarikI arWamayiMxi.
    4   ilA iMwa potIlo, yAMtI britiR vAwAvaraNaMlonu 155 nimuRAla nidivigala ‘hAmleVt’ nilici geVliciMxaMte axi xAni cakkaxanAniki nixarSaname!
    5   avakASaM vaccina vAriki eVks‌pojar‌kUdA vaswuMxi.
    
    >>> 

2. **wx to utf:**

::

    >>> con = wxConvert(order='wx2utf', lang='hin')
    >>> 
    >>> hin = """
    ... 1   xeSa ke kaI hissoM meM sUKe ke AsAra uwpanna ho gae hEM
    ... 2   aba waka mOsama viBAga sAmAnya bAriSa hone kI apanI BaviRyavANI para adZA huA WA lekina aba yaha xAvA pUrI waraha se KArija ho gayA hE
    ... 3   xeSa Bara meM aba waka huI bAriSa Osawa se Caha PIsaxI kama hE jabaki viBAga kA xAvA WA ki isameM 5 PIsaxI se jyAxA kamI nahIM hogI
    ... 4   isake calawe uwwara praxeSa paMjAba hariyANA rAjasWAna bihAra JAraKaMda Axi rAjya lagaBaga sUKe kI capeta meM hEM
    ... 5   lekina wakanIkI kAraNoM se inheM aBI sUKAgraswa GoRiwa nahIM kiyA gayA hE
    ... """
    >>> 
    >>> print con.convert(hin)
    
    1   देश के कई हिस्सों में सूखे के आसार उत्पन्न हो गए हैं
    2   अब तक मौसम विभाग सामान्य बारिश होने की अपनी भविष्यवाणी पर अड़ा हुआ था लेकिन अब यह दावा पूरी तरह से खारिज हो गया है
    3   देश भर में अब तक हुई बारिश औसत से छह फीसदी कम है जबकि विभाग का दावा था कि इसमें 5 फीसदी से ज्यादा कमी नहीं होगी
    4   इसके चलते उत्तर प्रदेश पंजाब हरियाणा राजस्थान बिहार झारखंड आदि राज्य लगभग सूखे की चपेट में हैं
    5   लेकिन तकनीकी कारणों से इन्हें अभी सूखाग्रस्त घोषित नहीं किया गया है
    
    >>> 

3. **work with conll:**

::

    >>> con = wxConvert(order='utf2wx', lang='hin', format_='conll')
    >>> 
    >>> conll = """
    ... 1       इसकी     यह      pn      PRP     cat-pn|gen-f|num-sg|pers-3|case-o|vib-का|tam-kA|chunkId-NP|chunkType-head|stype-|voicetype-      2     r6      _       _
    ... 2       ऊँचाई     ऊँचाई     n       NN      cat-n|gen-f|num-sg|pers-3|case-d|vib-0|tam-0|chunkId-NP2|chunkType-head|stype-|voicetype-       6     k1      _       _
    ... 3       केवल     केवल     avy     RP      cat-avy|gen-|num-|pers-|case-|vib-|tam-|chunkId-NP3|chunkType-child|stype-|voicetype-   4       lwg__rp _       _
    ... 4       1982    1982    num     QC      cat-num|gen-any|num-any|pers-|case-any|vib-|tam-|chunkId-NP3|chunkType-child|stype-|voicetype-  5       nmod__adj       _       _
    ... 5       मीटर     मीटर     n       NN      cat-n|gen-m|num-sg|pers-3|case-d|vib-0|tam-0|chunkId-NP3|chunkType-head|stype-|voicetype-       6     k1s     _       _
    ... 6       है       है       v       VM      cat-v|gen-any|num-sg|pers-3|case-|vib-है|tam-hE|chunkId-VGF|chunkType-head|stype-declarative|voicetype-active    0       root    _       _
    ... 7       ।       ।       punc    SYM     cat-punc|gen-|num-|pers-|case-|vib-|tam-|chunkId-BLK|chunkType-head|stype-|voicetype-   6       rsym    _       _"""
    >>> 
    >>> print con.convert(conll)
    
    1   isakI   yaha    pn	PRP cat-pn|gen-f|num-sg|pers-3|case-o|vib-kA|tam-kA|chunkId-NP|chunkType-head|stype-|voicetype-	2   r6	_   _
    2   UzcAI   UzcAI   n	NN  cat-n|gen-f|num-sg|pers-3|case-d|vib-0|tam-0|chunkId-NP2|chunkType-head|stype-|voicetype-	6   k1	_   _
    3   kevala  kevala  avy	RP  cat-avy|gen-|num-|pers-|case-|vib-|tam-|chunkId-NP3|chunkType-child|stype-|voicetype-   4	lwg__rp_    _
    4   1982    1982    num	QC  cat-num|gen-any|num-any|pers-|case-any|vib-|tam-|chunkId-NP3|chunkType-child|stype-|voicetype-  5	nmod__adj   _	_
    5   mItara  mItara  n	NN  cat-n|gen-m|num-sg|pers-3|case-d|vib-0|tam-0|chunkId-NP3|chunkType-head|stype-|voicetype-	6   k1s	_   _
    6   hE	hE  v	VM  cat-v|gen-any|num-sg|pers-3|case-|vib-hE|tam-hE|chunkId-VGF|chunkType-head|stype-declarative|voicetype-active   0	root	_   _
    7   .	.   punc    SYM	cat-punc|gen-|num-|pers-|case-|vib-|tam-|chunkId-BLK|chunkType-head|stype-|voicetype-	6   rsym    __
    >>> 

4. **work with tnt:**

::

    >>> tnt = """
    ... यों       RB
    ... सिंगल     JJ
    ... स्क्रीन    NNC
    ... थिएटर    NNP
    ... के       PSP
    ... दर्शकों    NN
    ... को       PSP
    ... अग्निपथ   NNP
    ... अधिक     QF
    ... नहीं      NEG
    ... भा       VM
    ... सकी      VAUX
    ... ।       SYM
    ... """
    >>> 
    >>> con = wxConvert(order='utf2wx', lang='hin', format_='tnt')
    >>> 
    >>> print con.convert(tnt)
    
    yoM RB
    siMgala	JJ
    skrIna	NNC
    Wietara	NNP
    ke  PSP
    xarSakoM    NN
    ko  PSP
    agnipaWa    NNP
    aXika	QF
    nahIM	NEG
    BA  VM
    sakI	VAUX
    .   SYM
    
    >>> 

5. **work with bio:**

::

    same as tnt or conll

6. **work with ssf:**

::
    
    to be implemented soon

7. **work with text files:**

::

    python runConverter.py --f text --l hin --s utf --t wx --i tests/text/hin-utf.txt --o tests/text/hin-wx.txt

    python runConverter.py --h
    usage: convertor_indic [-h] [--v] [--l language] --s source --t target
                           [--i input] [--f format] [--o output]
    
    wx-utf convertor for Indain languages
    
    optional arguments:
      -h, --help    show this help message and exit
      --v           show program's version number and exit
      --l language  select language [hin|tel|...] (3 letter ISO-639 code)
      --s source    select input-file encoding [utf|wx]
      --t target    select output-file encoding [utf|wx]
      --i input     <input-file>
      --f format    select output format [text|ssf|conll|bio|tnt]
      --o output    <output-file>

