- Information retrieval
	- Find a subset $R \subseteq D$ which is maximally relevant to $Q$ where $D$ is a collection of documents and $Q$ is a query
- Information extraction
	- Extract structured knowledge out of a document collection (such as entities, events, relationships, fact...)
- Ambiguity (= Mehrdeutigkeit)
	- Homograph (= written equally)
		- "The howling wind" vs "Wind your watch!"
	- Homophone (= Sounds equally)
		- "Late at night" vs "Medieval knight"

- Natural Language Processing
	- How to judge if a method is better than another one+
		- Intrinsic evaluation
			- Test a method in isolation by comparing the output with a predefined expectation (gold standard)
			- Example: Compare a system's judgment of good vs. bad reasons with multiple human decisions
		- Extrinsic evaluation
			- Test a method in use by embedding it into a larger system or experimental setup (e.g. a user Story)
			- Example: Let high school students write persuasive essays with and without the help of the system and compare their results

# Natural language text
### Text
- Script $\Sigma$ = {A, B, C, ..., a, b, c, ..., 0, 1, ...}
- Symbol or Character $s' \in \Sigma$
- String s = $s_{1}s_{2}...s_{n}$
- Message: String that follows a grammar
- Data: exchanged messages
- Text: written (or quasi-written) coherent data of a language
- Coherence: what makes a text semantically meaningful, connects the ideas arranges in a text

### Script and Language
#### Script
- Defines the "alphabet" (symbol set) $\Sigma$
- Alphabetic scripts: Latin, Greek, Cyrillic, ...
- writing direction: Left-to-right, right to left, top-to-bottom, ...

#### Language
- Determines the vocabulary and grammar
- Examples: German, English...

#### Properties of text
- Text type / genre: Textbook, scientific article, news item, social media post...
- Register: language variety used (e.g., dialect, jargon, formal...)
- Style: how a text is written (funny, polite, scientific style, ...)
- Domain/topic: biology, education, building spacecrafts, fantasy
- Time of writing: language changes over time

#### Text structure
1. Chapter/section
2. Paragraph
3. Sentence
4. Phrase
5. Word
6. Letter / Character

#### Character Encoding
DBs can only save sequences of 0 and 1
- Character encoding function $enc: \Sigma^{*} \rightarrow {0,1}^*$
- Character decoding function $dec: {0, 1}^* \rightarrow \Sigma^*$

- Typically: map each character separately based on a character set $\psi : \Sigma \rightarrow {0, 1}^*$ 
- A given text $T = c_{1}c_{2}...c_{n} \in \Sigma^{*}$ will be encodes as $enc(T) = \psi(c_{1})\psi(c_2)...\psi(c_{n})$ 

Example: encode $T = hallo$ in ASCII
- $enc(T) =$ 01101000 01100001 01101100 01101100 01101111 