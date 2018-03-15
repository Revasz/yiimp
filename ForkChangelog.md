[![Build Status](https://travis-ci.org/Revasz/yiimp.svg?branch=AllBranchesMerged)](https://travis-ci.org/Revasz/yiimp)

As of march, 2018 this fork is **100% compatible** with [*tpruvot's yiimp*](https://github.com/tpruvot/yiimp/tree/next).


This means, if you don't want to use all changes, you can fork from [*tpruvot*](https://github.com/tpruvot/yiimp/tree/next)<br/>
and merge only the patches you want from the corresponding branches of this fork.


Or you can fork from me and just use one of my branches, with the changes you want, as your default *master*<br/>
They are all, with some delay, *up-to-date* with [*tpruvot's*](https://github.com/tpruvot/yiimp/tree/next) commits.


If you want the *full-package*, use [*AllBranchesMerged*](https://github.com/Revasz/yiimp/tree/AllBranchesMerged) as your default *master*.


This fork is a *work-in-progress* project and can, but doesn't have to, contain untested code from time to time.<br/>
Use with caution.


_____


**Changes:**

	Fix:

		Payments: Prevent 9 decimals on failed payments.

		Changed file:
				/web/yaamp/core/backend/payment.php


**Forked from:**
https://github.com/AltMinerNet/yiimp/tree/AltMinerNet-patch-failed-payments


_____


	Fix:

		Fixed an issue where the AverageIncrement function could return 80%
		of the actual value when the function receives a 0 result from a market.

		Changed file:
				/web/yaamp/core/backend/markets.php


**Forked from:**
https://github.com/Jaerin/yiimp

_____


	Fix:

		Late Transactions.
		All coins, including ones with sell on bid, shouldn't send late transactions to exchanges.
		Update lastsent after a valid transaction and not before.

		Changed file:
				/web/yaamp/core/backend/sell.php


**Forked from:**
https://github.com/Infernoman/yiimp/tree/patch-5


_____


	Add:

		Stratum: Optional alert when stratum starts/restarts.

		Changed file:
				/stratum/config/run.sh


**Forked from:**
https://github.com/crackfoo/yiimp/tree/patch-2


_____
	
	
	Add:

		Per user fees.

		Changed files:  
				/web/serverconfig.sample.php
				/web/yaamp/core/backend/blocks.php
				/web/yaamp/core/functions/yaamp.php


**Additional changes:** [PR #13](https://github.com/Revasz/yiimp/pull/13/commits/8fba1184f74af8db4f6b030830d000f47ae4c195)

**Forked from:**
https://github.com/Tristian/yiimp/tree/user-fees


_____
	
	
	Enhancement:

		Stats: A little refactoring, code style and fix for showing empty graphs.

		Changed files:
				/web/yaamp/modules/stats/graph_results_1.php
				/web/yaamp/modules/stats/graph_results_2.php
				/web/yaamp/modules/stats/graph_results_3.php
				/web/yaamp/modules/stats/graph_results_4.php
				/web/yaamp/modules/stats/graph_results_5.php
				/web/yaamp/modules/stats/graph_results_6.php
				/web/yaamp/modules/stats/graph_results_7.php
				/web/yaamp/modules/stats/graph_results_8.php
				/web/yaamp/modules/stats/graph_results_9.php


**Forked from:**
https://github.com/AlmazDelDiablo/yiimp/tree/fix_graphs


_____
	
	
	Enhancement:

		Renting: 
				  HTML 4 to 5.
				+ Redirection fix.
				+ Display only algorithm with coins.
				+ YAAMP_RENTING_MIN_BALANCE in serverconfig.php.

		Changed files:
				/web/serverconfig.sample.php
				/web/yaamp/defaultconfig.php
				/web/yaamp/modules/renting/RentingController.php
				/web/yaamp/modules/renting/admin.php
				/web/yaamp/modules/renting/all_orders_results.php
				/web/yaamp/modules/renting/balance_results.php
				/web/yaamp/modules/renting/index.php
				/web/yaamp/modules/renting/login.php
				/web/yaamp/modules/renting/orders_results.php
				/web/yaamp/modules/renting/settings.php
				/web/yaamp/modules/renting/status_results.php


**Forked from:**
https://github.com/phm87/yiimp/tree/phm87-renting-patch-1


_____
	
	
	Minor change:
		
		Reserved balances.

		Changed file:
				/web/yaamp/core/backend/sell.php


**Forked from:**
https://github.com/Infernoman/yiimp/tree/patch-1


_____
	
	
	Minor change:

		Stratum: sync changes from json-parser, prevent delete on NULL share.

		Changed files:
				/stratum/json.cpp
				/stratum/json.h
				/stratum/share.h


**Forked from:**
https://github.com/AltMinerNet/yiimp/tree/tuning


_____
	
	
	Minor change:

		Order algorithms alphabetical in yaamp.php.

		Changed file:
				/web/yaamp/core/functions/yaamp.php

_____


	Minor change/Add:

		  Travis-CI configuration for build checks.
		+ README.md formatting
		+ Add ForkChangelog.md

		Changed files:
				yiimp/.travis.yml
				yiimp/README.md
				yiimp/ForkChangelog.md

_____


**Donations are welcome & appreciated.**


	BTC: 1i6yhynkkaDN2Y1RiNoZRxcQkEELdePUV

	ETH: 0x222eD19EAA80eE530B55b3a8394cF841DFb41Af6

	XMR: 4AbuFAvg6wUKxH4uZafgcyJuUkksxiZBz1N8sNvtQbYNe9bDfCnSFxcPs3ZPfaeDzNc9rWorxw4piBvEpuKvWL8dPSJxcPu

	BCH: 1Po5XaiwZg8iWDjZDwoNU7M56DpxRmkmed


***Revasz,* 2018**
