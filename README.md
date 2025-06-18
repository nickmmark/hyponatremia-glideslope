# hyponatremia-glideslope

### 🏥 Medical Context
Hyponatremia is a common but potentially serious electrolyte disturbance among hospitalized patients. Correcting hyponatremia too rapidly can lead to serious complications such as [Central pontine myelinolysis (CPM)](https://en.wikipedia.org/wiki/Central_pontine_myelinolysis) and Osmotic Demyelination Syndrome (ODS). Avoiding these complications requires careful monitoring and titration of therapies. One challenge is defining precise sodium correction goals and determining if the correction is occuring as intended. This is fundamentally a data visualization problem, that can be solved with an interactive web-app.

### 📈 Solution
The patient's sodium values are displayed in an xy plot versus time. The safe rate of correction is shown as a ***glideslope***. The user can add more sodium values and see if they within the safe rate of correction. Values outside the safe correction range are highlighted. 
The user can use the default rate of sodium correction (6-8 mEq/L/day), a more cautious rate (4-6 mEq/L/day), a more aggressive rate (8-10 mEq/L/day), or even customize the rate.
Once the user has built the visualization they can either review it via the web app, copy it to the clipboard (to paste into the EHR), or print it out.

![](https://github.com/nickmmark/hyponatremia-glideslope/blob/main/sodium_correction_v1.gif)

### ⚙️ Implementation
- Uses [luxon.js](https://moment.github.io/luxon/#/) for handling date/times and [chart.js](https://www.chartjs.org/docs/latest/charts/line.html) for displaying the results. It uses the Luxon [Chart.js adapter](https://github.com/chartjs/chartjs-adapter-luxon) for easy interoperability between the two.
- Uses [the Asynchronous Clipboard API](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API) for pasting and the [window.print function](https://developer.mozilla.org/en-US/docs/Web/API/Window/print) for printing or export to PDF.

### ⚠️ Limitations
Although the original reports of osmotic demyelination syndrome suggested that rapid correction of sodium (>12 mEq/L/day) more recent studies suggest that ODS can occur with slower rates of correction.
Even patients with relatively slow correction of hyponatremia can develop CPM/ODS.
https://evidence.nejm.org/doi/full/10.1056/EVIDoa2300107
https://evidence.nejm.org/doi/full/10.1056/EVIDoa2200215

### 🚧 Features to Add
[ ] It would be helpful to add therapies on the graph, for example:
- when was saline or free water given & how much
- ideally I could add a weight based calculator to *estimate* how much a given free water bolus would be expected to decrease the sodium
- when was ddAVP given --> show the expected half life of the drug

[ ] Make it possible to save the graph or share with someone else
- would need to persist the data (e.g. on a server) and have a login
- alternatively could have a "share" button that included the data in the hyperlink?

[ ] Add a watermark to the graph

### 🪪 License
MIT License - free to reuse (including commercially) but please acknowledge where you got it!

### 📚 References
Original report of Osmotic Demyelination Syndrome
https://www.nejm.org/doi/abs/10.1056/NEJM198606123142402

