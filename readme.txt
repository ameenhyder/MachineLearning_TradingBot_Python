Task:
	Make high frequency trading bot based on Gradient Boosting Algo.

Useful Links:
	Other Courses:
		https://www.udemy.com/course/algorithmic-trading-with-python-and-machine-learning/
	
	Source code of Bot:  
		https://github.com/PacktPublishing/Machine-Learning-for-Algorithmic-Trading-Second-Edition/blob/master/12_gradient_boosting_machines/11_intraday_model.ipynb
		
		Issue: The data set used in the source code uses more columns and we are hitting an API that returns only 6 columns. 
	
	Main Source Repo:
		https://github.com/PacktPublishing/Machine-Learning-for-Algorithmic-Trading-Second-Edition/tree/master/12_gradient_boosting_machines
		
		https://github.com/stefan-jansen/machine-learning-for-trading

		(This main repo contains the source code also)

	Feature Engineering Code:
		https://github.com/PacktPublishing/Machine-Learning-for-Algorithmic-Trading-Second-Edition/blob/master/12_gradient_boosting_machines/10_intraday_features.ipynb

		Through above code the features for main models is built.

	Further Documentation on Boosting Strategy:
		https://github.com/PacktPublishing/Machine-Learning-for-Algorithmic-Trading-Second-Edition/blob/master/README.md#12-boosting-your-trading-strategy


	API Documentation:
		https://www.alphavantage.co/documentation/

		https://www.alphavantage.co/documentation/#symbolsearch

		API key: TDJCJMSABXYSLRSP


Work Flow:
	- Read documentation and try to make sense of it first.

		Stefan Janson has wrote a book Machine Learning for Algorithmic Trading in which has has 
		built several ml models. 

		Github repository contains all the details and source code.

		He has used algo-seek data to built gradient boosting model that is 1min ticker based NASDAQ 100 
		dataset.

	- Read documentation of above dataset to make sense out of it and compare with our API data. 
		
		Documentation Link: https://us-equity-market-data-docs.s3.amazonaws.com/algoseek.US.Equity.TAQ.Minute.Bars.pdf

		Download Link: https://algoseek-public.s3.amazonaws.com/nasdaq100-1min.zip

	- Features Fetched from Original Data Set:
		
		This data set represents the summary of all the trades done in one minute of one ticker (ticker means company)

		first:	firsttradeprice:	Price of the first trade
		high:	hightradeprice:		Price of the highest trade
 		low:	lowtradeprice:		Price of the lowest trade
		last:	lasttradeprice		Price of the last trade
		price:	volumeweightprice:	Trade volume weighted average price (Need to see but is price column)
		volume: volume:			Total number of shares traded
		up:	uptickvolume:		Total number of shares traded with Uptick (Trade Price > Last Trade Price)
		down:	downtickvolume:		Total number of shares traded with Downtick(Trade Price < Last Trade Price)
		rup:	repeatuptickvolume:	Total number of shares traded with Repeat Uptick(Trade Price == Last Trade Price & Last Tick Direction == Up)
		rdown:	repeatdowntickvolume:	Total number of shares traded with Repeat Downtick (Trade Price == Last Trade Price & Last Tick Direction == Down)
		attask:	tradeattask:		Sum of trade volume that occured at or above the Ask
		atbid: 	tradeatbid		Sum of trade volume that occured at or below the Bid
		date:	made from date_time (Date + TimeBarStart)

		index: ticker + date_time

	- Features returned by API:
		index --> ticker + datetime
		datetime --> date
		open --> first
		high --> high
		low  --> low
		close--> last
		volume --> volume

	 - For installing ta-lib library run following in anaconda prompt:
		$ conda install -c conda-forge ta-lib

	 - Features Used in the Final Data Set:

		They are all engineered, will be engineered afterwards. 

		minute
		ret1min
		ret2min
		ret3min
		.
		.
		.
		ret10min
		fwd1min
		rup
		rdowm
		BOP
		CCI
		MFI
		STOCHRSI
		slowd
		slowk
		NATR
		trades_bid_ask	
		

	- Prepare the dataset according to the requirements of the model in the main source code
		done.

		issues: date_time is used in main code. It is derived from date_timebarstart which is made as index. 
			
			Hence, date_time is an index with date and time both. (main function main code)

			date(datetime64[ns] format) is made from date_time with date part only. (line 14 main code)

			date column is changed afterwards in factorize format (22 line main code)

			minute column is also made from date_time index (23 line main code)



			and our code has datetime. Need to decipher what each means

	- Run the code. 

AMD ADBE ABNB ALGN AMZN AMGN AEP ADI ANSS AAPL AMAT ASML TEAM ADSK ATVI	ADP AZN	BKR AVGO BIIB BMRN BKNG	
CDNS CHTR CPRT , CSGP CRWD CTAS	CSCO CMCSA COST	CSX CTSH DDOG DXCM FANG	DLTR EA	EBAY ENPH EXC FAST GFS	
META FISV FTNT GILD GOOG GOOGL HON ILMN INTC INTU ISRG MRVL IDXX JD KDP KLAC KHC LRCX LCID LULU	
MELI MAR MCHP MDLZ MRNA	MNST MSFT MU NFLX NVDA NXPI ODFL ORLY PCAR PANW PAYX PDD PYPL PEP QCOM	REGN RIVN  ROST 
SIRI SGEN SBUX SNPS TSLA TXN TMUS VRSK VRTX WBA WBD WDAY XEL ZM ZS
























		