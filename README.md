# Co-movement-in-Music-Sentiment-and-Policy-Uncertainty
We use arallel processing to scrape lyrics and Stanford NLP to extract sentiment
extract music lyrics from all publicly available songs from 1995 to 2018, compute each song's sentiment using CoreNLP built-in software, and compare the evolution of average annual music sentiment to the evolution of average annual policy uncertainty in the US.
The prior is that higher policy uncertainty is associated to more negative lyric sentiment (the higher the sentiment score, the higher the "positiveness". Policy uncertainty is calculated monthly using news and economic indicators as components.
We compute music sentiment as a weighted sentiment score using the probability that a given lyric is classified as Very Negative (=1), Negative (=2), Neutral (=3), Positive (=4), and Very Positive (=5). The Stanford NLP sentiment analysis toolkit outputs a sentiment probability distribution that we use to weight the integer scores into one overall score, which we then average on an annual basis.


Data: Music lyrics and economic + political ("policy") uncertainty index
Text stream of song lyrics + song metadata (artist, title, album, year) from 1995 to 2018
Monthly US policy uncertainty index from 1995 to 2018
Data Sources:
Music Lyrics (Lyrics Wiki), a comprehensive music lyric website:
http://lyrics.wikia.com/wiki/Category:Albums_by_Release_Year
US Policy Uncertainty Index (EPU), computed monthly for US and other countries by Baker, Davis, and Bloom: http://www.policyuncertainty.com/us_monthly.html
Data Analysis:
Compute, via NLP, mean annual music sentiment.
Showing evolution of music lyric sentiment on time.
Looking at co-movement of sentiment and political uncertainty indexes over time
Parallelization Strategy:
Divide into even, only mod(5) and neither, years for scraping lyrics, using a shared list among tree producer processes and a consumer process sharing a queue and other appropriate data structures.
