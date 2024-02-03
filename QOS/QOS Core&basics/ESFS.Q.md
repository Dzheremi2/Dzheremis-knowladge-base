[ESFS.Q](Filesystem%20Hierarchy.md) is a modification of [ESFS](ESFS.md) created for working with Quantum Data Elements(QDE) and with Quantum Superb States(QSS) It works with quantum qubits straight and uses qubits's Local Quantum Qubit Index(L2QI) which can storage up to $512^{512}$ files of any size

>[!INFO]
>ESFS.Q created by group of scientists in University of Iceland(Háskóli Íslands(Hí)) as better replace for Quantum Data Filesystem(QDFS) by IBM

>[!NOTE] Note
>ESFS.Q is a physical filesystem

>[!WARNING] ESFS.Q difference from ESFS
>ESFS.Q, unlike ESFS, is b-tree filesystem, which support momentum snapshots and (from ESFS.Q v6.0) [QOS](QOS⚛️.md)-specific feature called **Derivatives**. It's like default ESFS.Q's snapshots but better and stored more organized 

>[!IMPRT] Important
>ESFS.Q as ESFS's derivative can be only mounted to ESFS partition as physical filesystem, because it uses ESFS's functionality an binary API for accessing [ALR](ALR.md) returned data

>[!TIP] Fun fact
>$512^{515}$ files equals
>`14 002 965 526 155 144 834 555 305 452 685 214 372 866 082 888 911 214 819 410 098 563 166 364 393 430 339 704 954 316 846 760 882 417 420 604 004 588 805 172 709 668 950 479 443 731 801 102 542 528 740 113 036 510 299 444 061 547 747 539 391 052 523 594 629 678 962 987 431 385 091 951 024 344 687 624 116 958 504 831 353 788 456 858 187 662 249 641 364 321 767 348 607 606 502 983 077 596 886 259 472 559 892 509 340 453 479 591 701 669 341 690 610 010 199 752 681 859 969 642 725 277 394 461 284 724 377 187 107 117 253 177 142 493 474 639 946 364 494 226 253 006 015 222 273 057 859 996 893 954 087 112 388 911 638 079 340 740 307 953 400 728 723 420 436 588 952 155 758 688 261 952 181 120 583 722 524 183 166 457 598 150 762 152 371 703 020 012 995 588 938 072 866 897 073 390 632 452 049 784 351 496 937 636 259 712 515 524 623 518 773 707 258 808 280 520 421 766 533 723 982 678 808 205 124 377 338 390 350 147 232 981 694 928 107 493 357 143 336 100 099 345 127 583 310 326 317 513 361 407 701 585 332 291 704 561 598 012 157 109 134 338 690 845 941 606 929 566 579 109 845 648 752 432 227 530 123 144 780 633 008 215 865 200 107 064 955 296 873 959 439 674 874 263 446 726 724 444 594 593 399 440 980 900 885 790 456 007 303 431 910 585 281 124 234 213 951 629 658 205 321 241 942 054 284 455 065 419 268 372 128 178 209 253 142 263 303 100 509 032 020 839 738 717 162 419 633 361 923 319 257 010 022 504 665 335 926 405 622 345 740 884 671 364 959 272 460 376 791 398 153 022 984 421 227 494 300 704 089 333 484 168 581 053 903 671 324 229 299 871 114 933 203 089 732 015 328 195 933 736 811 542 888 636 618 070 746 229 101 551 946 063 862 190 952 517 481 681 820 714 828 448 743 184 805 157 114 555 460 571 190 275 103 234 955 695 251 063 616 575 057 295 286 339 621 140 306 864 204 977 859 618 146 869 750 759 448 354 484 860 806 496 256` files can store just one qubit😃

But these **↑** has it's own drawback, this number is not real number of file that can be stored in qubit, because we store qubit internal metadata in [rootBIN](rootBIN.md)/qb/ so rootBIN is *binary* partition and it's size is limited by 25Gb, one metadata for one qubit index is like 2 Bit, so system can have only ***107 374 182 400 files***, so that is much too, i think! And, you should know, that every next generation of processors has more rootBIN size than previous, which is mean, that in future the count of file will grow, not bad!? 