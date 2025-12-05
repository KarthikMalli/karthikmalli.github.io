# LIS 572 Project, Fall '25

## Introduction 

A key theme in my ongoing research is the circulation of texts and written material. More specifically, I look at these currents in India. Being in the US creates a disconnect between my physical location and the "field", but there are still interesting sites of inquiry that present themselves when you least expect them.


Being on a university campus has made that abundantly clear. Many university libraries across the US, including the University of Washington (UW) library, have impressive collections of Indian language books, with rare collections often hard to source in India itself. Somehow, over 5000 miles away from where they were first printed, they sit contentedly on a shelf unnoticed by passers-by until once a decade, someone reads them.


But why are these books are here in the first place?

## "Food for Books"


The answer lies (as it usually does) in the archives. Shortly after World War II, the United States Government undertook a novel scheme to procure books from newly independent countries across the world in exchange for foodstuffs. This was done to better understand potential allies (and foes) in the emerging geopolitical reconfigurations of the time. Termed the "food for books" program, the books procured through this scheme found their way into the libraries of American universities, including the University of Washington (UW). India was a major source for books, in the 1950s and 60s.


Many of the books procured under PL 480 were from India and formed the foundation of well-funded centers for the study of India and South Asia at universities like UChicago and UPenn. These universities continue to dominate academic research on South Asian themes, from history to linguistics to anthropology.

## Library Collection


I began by reaching out to the South Asian Studies librarian at UW, Deepa Banerjee. I asked her if I could receive a dataset of UW's books in Indian languages, which I limited to Hindi, Bengali, Urdu, Marathi, Kannada, Telugu, Malayalam, Tamil, Punjabi, Gujarati, and Sanskrit (yes, that's a limited set). The data points I wanted were title, date of publication, publisher, date of acquisition, place of publication, language, and genre.


I chose the 11 languages of my focus from my knowledge of the primary literary languages of India in terms of literary output, population size, and newspaper readership. I felt it would be interesting to see what trends in acquisition exist along linguistic lines as a reflection of networks of book acquisition and academic interest.


Working with Deepa and Hana Levay, the collection assessment librarian, I received a large dataset containing all physical records at UW in these 11 languages. It had almost 10,000 entries!

## Data Cleaning


Almost immediately, I encountered a major issue. I was informed that the data in the UW library system did not accurately record acquisition data from before 2013. This made it impossible with the given dataset to trace the direct imprint of PL 480 on the library collection and say definitively how many books in the UW collection were acquired this way.


I pivoted to instead looking at trends in language collection, and using date of publication as a proxy for date of acquisition (with the assumption that books would be acquired shortly after publication, and the obvious fact that books cannot be acquired _before_ they are published). I was also very interested in the spatial distribution of the collection: which cities in India, South Asia, and the world are these books from? After all, my definition of "Indian languages" included many transnational languages, like Urdu, Tamil, Bengali, Sanskrit, and Punjabi.


I also had to clean the data, since the city data used multiple transliteration schemes, and historical city names. For example, Dihli and Dilli both point to New Delhi; Cennai and Madras both point to Chennai; Poona and Punyanagar point to Pune. This, unfortunately, had to be done manually. I used OpenRefine for this (mindnumbing) task. I then "sliced" the data for the top 150 cities by book entries.


I also had to clean publication date data. The data included entries using three major non-Gregorian calendar styles: Hijri (~622), Fasli (~590), and Vikram Samvat (~56). Their Gregorian equivalent was supplied, in square brackets. To only capture the Gregorian entry, I had to devise a complex regex pattern that isolated dates from 1800-2000 and 2001-2025, which would definitively ignore Hijri and Fasli dates and VS dates greater than 2025.

## Analysis


With that work done, I could move on to generating visualizations. 


The most simple was a weighted bar graph of each of the 11 languages by book entry count, to see which languages are acquired more. Unsurprisingly, Hindi, Urdu, and Bengali top the list. I was somewhat surprised to see Malayalam at the bottom of the list, since it the language has a very robust publishing and reading culture in India, with a larger readership than languages with twice or even three times more speakers. This graph shows that the library collection reflects the visibility (and invisibility) of languages in US academia rather than their readership or publishing health.

<iframe src="UW-Bar-Line.html" text="Indian Language Books by Book Numbers" height="700" width="700"></iframe>

I created a line graph to see the volume of books in different languages across publication year, to get a sense of when books in the collection are from. I was surprised that it's _after_ 2010 that the numbers are highest; I was expecting the 50s and 60s to be better represented. I was also surprised that there was little in the collection from the 1800s. Maybe UW was not a very substantial beneficiary of PL 480 after all.

<iframe src="UW-Lang-Line.html" text="Year of Publication by Books, by Language" height="700" width="700"></iframe>

I was particularly excited to create a map of the collection using Leaflet, a library I had seen in the past and ended up playing around with on smaller side projects before this one (I also briefly read about in some technical readings for class). I used the cleaned city data with total book count for this, giving each city a circle marker weighted and colored by total book count to highlight the difference in volume.

<iframe src="UW-Book-Map.html" text="Map of Indian Language Books by Publication Location" height="700" width="700"></iframe>


Unsurprisingly, national and state/provincial capitals like Delhi, Lahore, Dhaka, and Chennai are overrepresented in the data. However, it was the smaller centers that I see as more interesting.

It was particularly gratifying to see how the map points represented well-documented nodes in literary production and traffic in different Indian languages, even if this importance was not reflected in their political status or demographic size. For example, Bijnor, a minor city with only ~115,000 people is the source of 35 books in the collection. The city, an important market town in British India, was once home to a thriving publishing industry in Urdu. Bareilly and Deoband, both in the same state of Uttar Pradesh, show up on the map for similar reasons. Any scholar of Urdu would see the small dots on the landscape of northern India and immediately make this connection.

It was funny to see distant Osnabrück in Germany show up on the map too...

# Some Issues

It's important to note that the data I worked with is not publicly available or viewable, but students at UW can request library data from librarians in a similar process to my own. This will likely not be an option for people who are neither students nor staff at UW. My presence within the university system affords me this opportunity that researchers back in India itself cannot make use of. This is unfortunately an infrastructural issue that scholars from non-Western countries in Western academia are all too familiar with, and it sustains a system of knowledge asymmetry.

## What's Next?

As a larger project, I would be super interested in doing a similar analysis across major US university libraries, to see if there are discernable trends in what languages or regions are better represented where, or if certain decades show more acquisition rates than others. I am also curious if there is another way to find the elusive 1950s-1960s data -- perhaps other libraries have it -- and see once and for all what books were acquired under PL 480 and what genres they represent. Perhaps their choices represent what was deemed geopolitically significant at the time, or maybe it was just whatever was being offloaded by Indian publishers.

With that, we're back to the question: what books are people reading, and where do they come from?

I'd like to let these visualizations try and answer that, if even only in part.
