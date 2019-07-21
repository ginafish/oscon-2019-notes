# Paco Nathan - Overview of Data Governance
derwen.ai/s/6fqt

Used to be a pretty dry topic, but this year has had a lot of change
Public sector might be head of industry in this right now (!)

Data governance
It's hard, and has had a lot of false starts
2018 had basically more data breaches than ever before, and saw GDPR going into effect.  Wall St Journal: "a global reckoning on data goernance"

Different continents has different priorities
China - veractiy of data (bc government)
EU - storage and analysis (bc history)
NA - consequences of acting on data (bc lawyers)
Some differences between continents on what data solutions they are looking at

2001 - generation of developers equate database w/ relational and that legibility of systems == legibility of the data
State/governance body institute things that require legibility of systems
"Tech unicorns" moved to NoSQL, particularly because of RDBMS pricing
Data was more of an afterthought
Got the "move fast and break things" mindset - code first, data last

Magical new C-level role CDO (Chief Data Officer) will solve everything!

FAIR data guidelines - for reproducible research, and industry needs more of that
Mark D. Wilkinson (?)

DCAT - W3C standards for metadata, describe datasets in data catalogs, how to describe dataset, who's using data and why, etc
adrf-onto < repo for this

ODPi Egeria - Apache Atlas is a native reference implementation
"Data systems pub sub"
Validate data exchange
"The Case for Open Metadata" Many Chessell

US Govmnt Initiatives
US Federal Data Strategy
strategy.data.gov < they're looking for input
Also, they're working on inter-dept data collection

AI is changing things!  Being compared to the invention of electricity.

Amundsen - from Lyft, data discovery and metadata
WhereHows - from LinkedIn data discovery and lineage
Marques - WeWork (and StitchFix, etc), collection, aggregation, metadata visualization for data ecosystem
Databook - Uber, manage metadata about given datasets (not open source yet)

Jupyter - make datasets and projects, metadata exchange and privacy-aware telemetry from notebook usage
Dataset registry, metadata service
Telemetry is plugable

ML upcoming issues:
Models degrade once exposted to live customer data
attack surfaces only vagely understood
"Why?" requires statistic expertise
Incoming ethics and compliance issues
Product management still being developed
