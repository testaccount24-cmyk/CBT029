# CBT029
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 029 IS A PROCEDURE TO ENLARGE THE VTOC OF AN ACTIVE       *   FILE 029
//*           PACK FROM MR SAM GOLOB.  THIS FILE IS IN IEBUPDTE     *   FILE 029
//*           SYSIN FORMAT.                                         *   FILE 029
//*                                                                 *   FILE 029
//*           email:  sbgolob@cbttape.org                           *   FILE 029
//*                                                                 *   FILE 029
//*           -----------------------------------------------       *   FILE 029
//*    NOTE:  The procedure in this file may now be obsolete.       *   FILE 029
//*           -----------------------------------------------       *   FILE 029
//*                                                                 *   FILE 029
//*           It seems that on current z/OS systems (we have        *   FILE 029
//*           z/OS 2.5 right now) there is an EXTVTOC function      *   FILE 029
//*           in IBM's ICKDSF program which can expand the VTOC     *   FILE 029
//*           of a disk pack.  The function called NEWVTOC will     *   FILE 029
//*           move the VTOC.  Our procedure would therefore not     *   FILE 029
//*           be necessary on those systems (although it would      *   FILE 029
//*           probably still work).                                 *   FILE 029
//*                                                                 *   FILE 029
//*           An example of how to use the ICKDSF method of         *   FILE 029
//*           expanding the VTOC and the VTOC Index, may be         *   FILE 029
//*           found in member $ICKDSF in this dataset.              *   FILE 029
//*                                                                 *   FILE 029
//*           But look in the IBM manual, just to be sure.          *   FILE 029
//*           The considerations we have talked about here,         *   FILE 029
//*           apply there as well.  (E.G. moving of datasets        *   FILE 029
//*           that are adjacent to the current VTOC)                *   FILE 029
//*                                                                 *   FILE 029
//*           z/OS  Device Support Facilities (ICKDSF) -            *   FILE 029
//*           User's Guide and Reference                            *   FILE 029
//*                                                                 *   FILE 029
//*    DESCRIPTION:                                                 *   FILE 029
//*                                                                 *   FILE 029
//*           THIS PROCEDURE PRESENTS A "COOKBOOK-STYLE" RECIPE     *   FILE 029
//*           FOR ENLARGING THE VTOC OF AN ACTIVE DASD PACK.  THE   *   FILE 029
//*           VTOC INDEX HAS TO BE DEACTIVATED FIRST.  EVERYTHING   *   FILE 029
//*           IS HERE, AND ALL THE "INGREDIENTS" IN THE RECIPE      *   FILE 029
//*           ARE ON THIS TAPE.  IT'S AN EASY TO FOLLOW PATH.       *   FILE 029
//*           ONCE YOU'VE DONE IT A FEW TIMES (BEING CAREFUL OF     *   FILE 029
//*           COURSE) IT'S A PIECE OF CAKE.                         *   FILE 029
//*                                                                 *   FILE 029
//*           IT IS ASSUMED THAT IF YOU ARE DOING THIS, THEN YOU    *   FILE 029
//*           ARE A "SYSTEM DOCTOR" AND YOU HAVE ACCESS TO APF-     *   FILE 029
//*           AUTHORIZATION OF TSO COMMANDS AND BATCH PROGRAMS.     *   FILE 029
//*                                                                 *   FILE 029
//*           THE PROCEDURE INVOLVES BUILDING AN EXTENSION TO THE   *   FILE 029
//*           END OF THE EXISTING VTOC.  THEREFORE, ANY DATASETS    *   FILE 029
//*           LYING ON THE TRACKS FOLLOWING THE END OF THE VTOC,    *   FILE 029
//*           HAVE TO BE MOVED OUT OF THE WAY.                      *   FILE 029
//*                                                                 *   FILE 029
//*           SEE MEMBER $RECEIVE TO CREATE A LOAD LIBRARY THAT     *   FILE 029
//*           CONTAINS ALL THE NECESSARY LOAD MODULES.  YOU WILL    *   FILE 029
//*           HAVE TO APF-AUTHORIZE THIS LIBRARY, OR COPY ITS       *   FILE 029
//*           MODULES INTO AN APF-AUTHORIZED LOAD LIBRARY.          *   FILE 029
//*                                                                 *   FILE 029
//*           SEE MEMBER DISKMAP FOR FURTHER DETAILS ON HOW TO      *   FILE 029
//*           RUN THE DISKMAP PROGRAM (SO YOU CAN SEE WHERE THE     *   FILE 029
//*           PLACEMENT OF THE VTOC IS).                            *   FILE 029
//*                                                                 *   FILE 029
//*           JUST REMEMBER THAT THE DISKMAP PROGRAM HAS TO BE      *   FILE 029
//*           APF-AUTHORIZED.                                       *   FILE 029
//*                                                                 *   FILE 029
//*           THE MEMBER OF THIS PDS CALLED NARRATIV, CONTAINS      *   FILE 029
//*           THE ACTUAL INSTRUCTIONS ON HOW TO PROCEED.            *   FILE 029
//*                                                                 *   FILE 029
//*           I DON'T RECOMMEND USING THE IBM PROGRAM IEHLIST,      *   FILE 029
//*           (MEMBER IEHLIST IN THIS PDS) TO GET A VTOC MAP.       *   FILE 029
//*           IN MY OPINION, THE IEHLIST REPORT IS VERY UNCLEAR.    *   FILE 029
//*           USE THE SUPPLIED PROGRAM DISKMAP FOR THIS PURPOSE.    *   FILE 029
//*                                                                 *   FILE 029
```
