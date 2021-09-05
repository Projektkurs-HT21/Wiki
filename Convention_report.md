# Kod-konvention Rapport
Här är en kort beskrivning om hur LaTeX koden ska skrivas i rapporten och hur filer ska struktureras

För att göra det enkelt för alla att jobba tillsammans i rapporten är det viktigt att alla följer följande konvention för att förhindra merge konflikter och för att det ska vara lätt att följa med i vart alla filer ligger.

## Filstruktur i rapporten

Alla sektioner, subsektioner och subsubsektioner ska ligga i sina egna filer och mappar. En sektion ska ligga i en egen fil i en egen mapp under mappen ```Report```. En subsektion ska ligga i sin egen fil under sectionens mapp osv. Detta för att filerna i projektet ska vara såpass isolerade som möjligt, för att förhindra merge konflikter.

## Namn på filer och mappar
Namn på filer och mappar ska vara densamme som sektionen som ligger i, med versaler på samma ställen och ```_``` istället för mellanslag. Includen i LaTeX uppskattar det, då den inte gillar mellanslag.

## Inkluderande av filer
För att inkludera en fil i rapporten används LaTeX kommandot ```\input{Filepath}```. _Filepath_ i detta fall filepathen relativt till ```index.tex```, som är vårt huvuddokument. Inkluderandet av en sektion fil görs i ```index.tex``` och inkluderandet av subsektioner osv görs i sektion filen som subsektionen tillhör.

## Exempel
Säg att du vill lägga till sektionen _Improving the system_. Det är en sektion, så dess mapp ska ligga under _Report_ och den ska heta ```Improving_the_system```. I dess mapp skapar du filen ```Improving_the_system.tex``` och i den filen lägger du din ```\section{Improving the system}```. För att inkludera sektionen i dokumentet lägger du till ```\input{Improving_the_system/Improving_the_system.tex}``` i ```index.tex```.

Vill du senare lägga till subsektionen _Integrations_ skapar du en mapp under ```Improving_the_system``` med namnet ```Integrations```. I mappen lägger du en fil vid namn ```Integrations.tex``` och i den filen lägger du din ```\subsection{Integrations}```. I ```Improving_the_system.tex``` lägger du till ```\input{Improving_the_system/Improving_the_system/Inregrations.tex}```.

Filstrukturen blir då.

    Report/
        index.tex
        Improving_the_system/
            Improving_the_system.tex
            Integrations/
                Integrations.tex
