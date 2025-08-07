---
layout: post
title: Great Circle to Rhumb Line Converter
subtitle: A Tool That Converts GC Tracks to RL Tracks in Route Files 
image: https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/GC%20to%20RL%20Thumbnail.png
---

When I joined <b>Nautilus Labs</b> in 2022, the company was still in its early stages. Like many startups at that phase, Nautilus relied on a combination of quick fixes and auxiliary tools while the core product was still under development. After settling in, I noticed several opportunities to both enhance existing systems and build new ones from scratch.

One of the first tools I developed was <b>Great Circle to Rhumb Line Converter</b>—a Python-based <b>Jupyter Notebook</b> script designed to parse route files (in both <b>RTZ</b> and <b>CSV</b> formats) and automatically convert all <b>Rhumb Line</b> segments to <b>Great Circle</b> tracks.

Before diving into the tool’s functionality, here are some key navigation terms that provide important context:

<b>Waypoints:</b>
Specific geographic coordinates (latitude and longitude) that define key turning points or positions along a planned route. Ships navigate from one waypoint to the next as part of their voyage plan.

<b>Route File:</b>
A digital file containing a sequence of waypoints, legs (segments between waypoints), and possibly metadata such as speed settings or safety parameters. These files are used in <b>ECDIS</b> (Electronic Chart Display and Information Systems) or voyage planning software to outline a vessel’s intended path.

<b>CSV File (Comma-Separated Values):</b>
A plain text file format that organizes data in a tabular structure, where each line represents a data entry and values are separated by commas. In maritime contexts, CSVs may include waypoints, weather forecasts, or log data.

<b>RTZ File (Route Exchange Format):</b>
A standardized format <b>(IEC 61174:2015)</b> used for exchanging route data between ships and shore-based systems. It includes waypoints, legs, safety parameters, and metadata, ensuring consistency across different <b>ECDIS</b> platforms.

<b>Rhumb Line (RL):</b>
Also known as a <b>Loxodrome</b>, this is a line that maintains a constant compass bearing, crossing all meridians at the same angle. While easy to follow, it is not the shortest route over long distances.

<b>Great Circle (GC):</b>
The shortest path between two points on a sphere. Unlike a rhumb line, a great circle route constantly changes its compass bearing. It is commonly used in long-distance ocean navigation to reduce travel time and fuel consumption. Also known as a <b>Orthodrome</b>.

<b>Loxodrome:</b>
A synonym for Rhumb Line—a path of constant compass direction. It is simple to navigate but longer over great distances.

<b>Orthodrome:</b>
Another term for Great Circle. It represents the true shortest distance between two points on the Earth’s surface. <b>"Orthodromic navigation"</b> refers to the practice of navigating using great circle routes.

<b>TCE (Time Charter Equivalent):</b>
A performance metric used in the shipping industry to calculate a vessel’s daily earnings, allowing for comparison across different voyage types.

<h4 style="text-align: center;"><b><i>TCE = (Voyage Revenue – Voyage Expenses) / Voyage Duration (days)</i></b></h4>

<b>Net Profit:</b>
The remaining earnings after subtracting all voyage-related expenses from total revenue. These expenses can include fuel, port fees, crew wages, and insurance.

<h4 style="text-align: center;"><b><i>Net Profit = Voyage Revenue – Voyage Expenses</i></b></h4>

<b>ETA (Estimated Time of Arrival):</b>
The expected arrival time of a vessel at a specific waypoint, port, or destination. ETA is critical for voyage planning, logistics, and port coordination.


At Nautilus Labs, one of our core offerings was voyage optimization—the process of optimizing a vessel’s transit to align with specific client objectives. These objectives could include maximizing <b>Time Charter Equivalent (TCE)</b>, maximizing <b>Net Profit</b>, or ensuring the vessel arrives precisely at a <b>target ETA</b>. The platform achieved this by recommending the ideal shaft speed that would help the vessel meet those targets.

To generate these recommendations, the first essential input was the vessel’s planned route. The route file enabled the platform to calculate the distance to be traveled and evaluate the weather conditions (such as <b>wind</b>, <b>wave</b>, and <b>current</b>) the vessel would encounter. Combined with the vessel’s historical performance data—specifically its speed and fuel consumption—the system could then compute the optimal <b>shaft speed</b> required to achieve the desired outcome.

It should be clear that an accurate and realistic route—one the vessel actually intended to follow—was critical for reliable <b>voyage optimization</b>. Without it, the platform couldn’t assess upcoming weather conditions accurately or recommend the appropriate speed strategy. The optimization would be based on flawed assumptions, leading to suboptimal outcomes.

Uploading a route to our platform was relatively simple on the surface:

- For <b>RTZ</b> files, users could upload directly.

- For <b>CSV</b> files or other formats, waypoints could be copied and pasted into a dedicated input field.

However, there was a key limitation: the platform’s parser didn’t differentiate between Rhumb Line (RL) and Great Circle (GC) tracks. It failed to read metadata specifying the segment type, defaulting to interpreting all waypoints as Rhumb Line.

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/CSV%20file.png)
https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/CSV%20file.png

This posed a significant problem. If the original route contained Great Circle segments (which it often did), the platform would misinterpret them, resulting in inaccurate route modeling. To correct this, analysts had to:

- Open the original route file and manually identify Great Circle segments using metadata.

- Use a separate tool to convert each GC segment into a series of intermediate Rhumb Line waypoints.

- Integrate those converted segments back into the route manually in a spreadsheet.

- Copy and paste the full updated list into the platform.

While manageable for a route with one or two GC segments, this process became increasingly tedious and error-prone as the number of GC waypoints grew. With 10–15 GC segments, the workflow could consume hours. In extreme cases—where an entire route was made of GC tracks—it was virtually impossible to complete the task within a single day.

This bottleneck presented an opportunity for automation.

### Mapping the Pain Points and Solutions:

I realized that the most technically complex step—converting Great Circle tracks into Rhumb Line approximations—was already handled by a script we had in an existing internal tool. The real inefficiencies lie in the manual steps: checking the route, running conversions one-by-one, integrating them manually, and ensuring proper formatting.

To streamline this, I set out to map the pain points and design a solution to address each of them. My goal was to fully automate the process from file input to ready-to-upload route, eliminating time-consuming manual interventions and minimizing the risk of human error.

<b>Here’s a summary of the key pain points and potential solutions I identified:</b>

| **Processes**           | **Manual Step / Pain Point**                                                                    | **Automated Solution**                                                      |
|------------------------|------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| Identifying segment types | Manually read the metadata to determine which waypoints are Rhumb Line (RL) and which are Great Circle (GC). | Script automatically reads metadata and identifies RL and GC waypoints.    |
| Converting GC segments  | Manually convert each GC segment into a corresponding RL segment, one at a time.                 | Script converts all GC segments to RL segments in batch.                    |
| Integrating waypoints   | Manually insert the converted waypoints into the original route at the correct positions.       | Script auto-merges converted waypoints into correct positions.             |
| Visual validation       | No way to visually validate whether the converted route matches the original intent.            | Script plots both original and converted routes on an interactive map.     |
| File compatibility     | Separate workflows are required for different route file formats (e.g., CSV vs RTZ).             | Script supports multiple formats with a unified workflow.                   |

### Route Conversion Script Workflow:

I wrote a script in a <b>Jupyter Notebook</b> to automate and streamline the route processing workflow. Here's what the script does:

- Uses a simple UI to accept route files in `.rtz`, `.csv`, or `.txt` format.

- Identifies the uploaded file type by calling the `identify_file_type()` function.

- Converts the file into a standardized format using the appropriate function based on file type:
  
  - `Convert_RTZ()` for `.rtz` files
    
  - `Convert_CSV()` for `.csv` files
    
  - `Convert_TXT()` for `.txt` files
    
  - The conversion retains all relevant data such as waypoint number, latitude, longitude, and RL/GC segment type.

- Performs GC to RL conversion using the standardized format:
  
  - Detects which waypoints are Great Circle (GC) and which are Rhumb Line (RL) by reading metadata.
    
  - Converts each GC segment into multiple smaller RL segments (approximately <b>50 nautical miles per leg</b>).
    
  - Automatically inserts the converted waypoints into the correct positions in the route sequence.
    
  - Visualizes both the original and the converted route on an interactive map for comparison, validation, and anomaly detection.

- Outputs the final route:
  
  - Exports the full list of converted waypoints in structured <b>JSON</b> format.

### User Guide for the Script

I designed the tool with usability in mind, recognizing that it would be used by individuals from diverse backgrounds—including analysts, engineers, and product managers—many of whom may not have advanced technical or coding skills. To make it accessible:

- The user is not required to write or edit any code.
  
- All code cells are hidden from view to reduce complexity.
  
- The interface is simplified so that the entire workflow can be completed through just a few intuitive steps

  - Upload the route file using the <b>built-in UI</b>.
    
  - View the <b>interactive map</b> to visually compare the original and converted <b>routes</b>.
    
  - If the route looks correct, copy the <b>printed waypoints</b> and paste them into the designated input area in the platform.

  
### Route File Uploader UI:
![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/Route%20Upload.png)

### Interactive Map:
![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/GC%20to%20RL.png)

### Original vs Converted Waypoints:

![Crepe](https://raw.githubusercontent.com/Ekram49/Ekram49.github.io/refs/heads/master/img/GC%20to%20RL/Original%20vs%20Converted.png)

### Final Thoughts

This was the first tool I built at Nautilus, and it ended up having a tremendous impact. What started as a way to improve the workflow for me and my team quickly became something that was used widely across the company. Analysts, engineers, and product managers all found value in it, and it became a regular part of our day-to-day process.

Seeing how much it helped others—and hearing the positive feedback—was incredibly rewarding. It showed me how even a small, well-designed tool can solve a real problem and make people’s work easier. That experience motivated me to keep going. I went on to build several other internal tools to improve different parts of our workflow, and many of them were not only used and appreciated internally, but parts of their output were even incorporated into <b>client-facing products</b>.

This particular tool tackled a topic that can be a bit technical and niche. Some of the terms (like <b>Rhumb Line</b>, <b>Great Circle</b>, <b>RTZ</b>, etc.) may not be familiar to everyone, and the need for converting and validating routes might not be obvious right away. If anything here sparks curiosity or you'd like to talk more about how or why this was done, feel free to reach out—I'd be more than happy to chat!

Hopefully, I’ll be able to write about the other tools I worked on soon, in the same level of detail as this one — until then, I’ll catch you at the next waypoint!
