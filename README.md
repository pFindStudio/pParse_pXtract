# pParse_pXtract Docs

tags ： pFind

---
![RelationTree][1]
## pXtract
All of pXtract have same cmd arguments, so you can use them without any changes on your cmd arguments. 
However, pXtract_xml does not support centralize peaks(-c won't take any effect), in the meanwhile, pFind usually works on centralized peaks, therefore, you should use proteowizard(https://github.com/ProteoWizard/pwiz) **with peak picking filter on the top** as we showed in the following pictures.

### Wiff
Xtract_wiff is deprecated in 2019, since the API that pFind used is out of warranty.

### Raw
We have 3 versions of Xtract_raw to read data of Thermo instruments:
1. Xtract_raw with RawFileReader
2. Xtract_raw with MSFileReader, 64 bit
3. Xtract_raw with MSFileReader, 32 bit

- If you are a User of pFind/pGlyco:
	- If your software is installed before 2019, then you are using Xtract_raw with MSFileReader, 32 bit.
	- After 2019, you are using Xtract_raw With RawFileReader
- If you are a User of pLink/pTop:
	- If your software is installed before May, 2019, then you are using Xtract_raw with MSFileReader, 32 bit.
	- After May, 2019, you are using Xtract_raw with MSFileReader, 64 bit.

Note:

All of pXtract have same cmd arguments, so you can use them without any changes on your cmd arguments.

Xtract_raw with MSFileReader, both 64 bit and 32 bit, have the same output. However, Xtract_raw with RawFileReader, has slightly **different** output. Please be aware of this change.
To use Xtract_raw with MSFileReader, both 64 bit and 32 bit, you need to install MSFileReader 64 bit or 32 bit.

If you see the following error message, you need to **FULLY UNINSTALL** your MSFileReader, and install another version of MSFileReader Accordlingly.
```
[pXtract] <Exception>: MSFileReader should be 32/64 bit version corresponding to pFind.
```

Be aware to fully uninstall MSFileReader, since modify panel seems do not work well enough to install the exact MS-COM component.

### mzML
We use Xtract_xml to extrat data from mzml or mzxml transformed by proteowizard by the following settings showed in pictures.
![msconverGUISetting1][2]
If your ProteoWizard is rather old,
![msconverGUISetting2][3]
### mgf
We use Xtract_raw/pParse to read mgf and generate ms2/pf2 which contains the peaks information.
However, pBuild do not fully support mgf yet(4/12/2019). But you still can search mgf without any trouble, you just cannot visualize the result using pBuild. This issue will be solved in the future.

### logging
`Xtract_raw` with RawFileReader and `Xtract_xml` record their log into `$pFindInstallDir$/bin/xtract_raw.log` or `$pFindInstallDir$/bin/xtract_xml.log`

### Environment
1. If you are using xtract_raw with MSFileReader, please install MSFileReader
2. If you are using xtract_raw with RawFileReader, xtract_wiff, xtract_xml, you just need to install .Net Environment.
3. Xtract_xml cannot centralize peaks by itself, so you need to convert your data by ProteoWizard(https://github.com/ProteoWizard/pwiz) using specific settings.

### Difference
1. Xtract_raw with MSFileReader keeps the same output since 2012.
2. Xtract_raw with RawFileReader has slightly different output compared to MSFileReader, however, Xtract_raw with RawFileReader used the latest APIs from Thermo(Those APIs lead to the different results).

## pParse
We have several versions of pParse:
1. pParse2.0(original version of pParse+)
2. pParse2.2(Before 2018)
3. pParse2.5(Using SVM, rarely used)
4. pParse2.2 Rewrited(2018-)
5. pParseTop, only used by pTop

- If you are a User of pFind/pGlyco:
	- If your software is installed before 2019, then you are using pParse2.2(Before 2018).
	- After 2019, you are using pParse2.2 Rewrited.
- If you are a User of pLink:
	- You are always using pParse 2.0.
- If you are a User of pTop:
    - You are always using pParseTop.(Be aware of model refinement)

### logging
We put the log into `$RawDir$\pParsePlusLog.txt`.

### Difference
1. pParse2.0 keeps the same output since 2012.
2. pParse2.2 has slightly different output compared to pParse2.0 since we updated our scoring function.

## Common FAQs
### pXtract Exception: 32/64 bit version
First, you should make sure that you installed MSFileReader.

```
[pXtract] <Exception>: MSFileReader should be 32/64 bit version corresponding to pFind.
```
Second, If you have installed MSFileReader, and you see the error message above, you need to **FULLY UNINSTALL** your MSFileReader, and install another version of MSFileReader Accordlingly(Of course you can install both of them).

### Should I download pXtract/pParse?
Normally EVERY pSoftware contains pXtract, pParse and Other pSoftwares it requires, so you do not need to apply for it.

### Cannot use MZML or MZXML
Be aware to use ProteoWizard with the following settings:
![msconverGUISetting1][2]
If your ProteoWizard is rather old,
![msconverGUISetting2][3]

### Cannot open XXX
IF the file needs to be writtenm Then This file is occupied by another program. Please close any program occupied this File.
If the file needs to be read, Then this file do not exist. Please check whether your input is correct. 
If your input is correct, sometimes you need to delete all files generated by pFind, especially xxx.xtract and xxx.csv. Why you need to do that? Well, sometimes pSoftware use the existence of certain file types as an indicator of success. Therefore, if your task corrupted once and your mid files exist, some of crucial processes won't rerun again.

### pParse stopped with no Exception Message outputed?
Your DATA have unexpected ZERO!! The program collapses once it divided zero.
In some pParse versions, we carefully checked all possibilities of dividing zero. However, in some old versions we do not. 
The unexected ZERO happenes a lot in wiff data. If you meet this error, please download the latest software or share your error on https://github.com/pFindStudio/pParse_pXtract/issues or contact pparse@ict.ac.cn or pfind@ict.ac.cn .

### Any other error?
Please share your error on https://github.com/pFindStudio/pParse_pXtract/issues or contact pparse@ict.ac.cn or pfind@ict.ac.cn .


  [1]: https://raw.githubusercontent.com/pFindStudio/pParse_pXtract/master/pxtract_pparse_relation.png
  [2]: https://raw.githubusercontent.com/pFindStudio/pParse_pXtract/master/msconvertGUI1.PNG
  [3]: https://raw.githubusercontent.com/pFindStudio/pParse_pXtract/master/msconvertGUI2.PNG