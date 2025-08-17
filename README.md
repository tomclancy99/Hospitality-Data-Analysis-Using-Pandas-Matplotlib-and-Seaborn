# Hospitality Data Analysis Project

This repository contains a data analysis project focused on exploring hotel booking data to derive insights into revenue realization across various booking platforms. Built using Python with libraries such as Pandas, Matplotlib, and Seaborn, this project showcases data visualization and exploratory data analysis (EDA) techniques applied to a real-world hospitality dataset.

## Overview

The project analyzes a dataset of hotel bookings, including details such as booking IDs, property IDs, dates, number of guests, room categories, booking platforms, ratings, booking status, and revenue metrics (generated and realized). The primary visualization is a professionally styled pie chart that breaks down revenue realized by booking platform, offering actionable insights for hospitality businesses.

### Key Features
- **Data Loading and Exploration**: Utilizes Pandas to load and inspect the dataset.
- **Visualization**: Employs Matplotlib and Seaborn to create an advanced, customizable pie chart with a modern aesthetic.
- **Insights**: Highlights revenue distribution, potential data anomalies (e.g., negative guest counts), and platform performance trends.

## Dataset
The dataset (`df_bookings_all`) includes the following columns:
- `booking_id`: Unique identifier for each booking.
- `property_id`: Identifier for the hotel property.
- `booking_date`: Date the booking was made.
- `check_in_date`: Check-in date.
- `checkout_date`: Check-out date.
- `no_guests`: Number of guests (note: includes anomalies like negative values).
- `room_category`: Room type (e.g., RT1).
- `booking_platform`: Platform used for booking (e.g., direct online, others, logtrip).
- `ratings_given`: Customer ratings (where available).
- `booking_status`: Status of the booking (e.g., Checked Out, Cancelled).
- `revenue_generated`: Total revenue generated.
- `revenue_realized`: Actual revenue realized.

## Installation

To run this project locally, ensure you have the required dependencies installed. Follow these steps:

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/hospitality-data-analysis.git
   cd hospitality-data-analysis
   ```

2. **Set Up a Virtual Environment** (optional but recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**
   Install the required Python libraries using pip:
   ```bash
   pip install pandas matplotlib seaborn
   ```

4. **Prepare the Data**
   - Place your `df_bookings_all.csv` file in the project directory (or update the notebook to load from your data source).
   - Ensure the dataset matches the structure described above.

## Usage

1. Open the Jupyter Notebook:
   ```bash
   jupyter notebook Hospitality_domain.ipynb
   ```

2. Run the cells in sequence:
   - Cell 1: Imports required libraries (Pandas, Matplotlib).
   - Cell 2: Loads the dataset and generates the revenue realization pie chart with custom styling.

3. Explore the visualization:
   - The pie chart displays the percentage contribution of each booking platform to total revenue realized.
   - A legend on the right lists all unique booking platforms for reference.

## Code Highlights

### Key Visualization Code
The project features a professionally styled pie chart created with the following code snippet:

```python
import seaborn as sns

sns.set_style("whitegrid")
plt.figure(figsize=(10, 6), facecolor='#f0f4f8')
plt.rcParams['font.family'] = 'sans-serif'
plt.rcParams['font.size'] = 12
plt.rcParams['axes.edgecolor'] = '#333333'
plt.rcParams['axes.labelcolor'] = '#333333'

ax = df_bookings_all.groupby('booking_platform')['revenue_realized'].sum().plot(kind='pie', 
                                                                              autopct='%1.1f%%', 
                                                                              startangle=90, 
                                                                              colors=['#4a90e2', '#50c878', '#f5a623', '#ff6f61', '#a66bbe', '#d3a25b', '#e06699'],
                                                                              wedgeprops={'edgecolor': 'white', 'linewidth': 1.5},
                                                                              textprops={'fontsize': 10, 'color': '#333333'})

plt.title('Revenue Realized per Booking Platform', fontsize=14, fontweight='bold', pad=20, color='#333333')
plt.ylabel(None)
plt.axis('equal')
ax.grid(False)
plt.tight_layout()
ax.legend(labels=df_bookings_all['booking_platform'].unique(), loc='center left', bbox_to_anchor=(1, 0.5), fontsize=10, frameon=False)
plt.show()
```

### Styling Features
- **Custom Colors**: A curated palette enhances visual distinction.
- **White Edges**: Adds a polished look to pie wedges.
- **Legend**: Positioned outside for clarity.
- **Background**: Light gray (`#f0f4f8`) for a modern feel.

## Insights
- The pie chart reveals the proportional revenue contribution from each booking platform.
- Anomalies like negative guest counts suggest data quality issues that could be addressed in future iterations.
- Platforms like "others" may warrant further investigation due to their significant share.

## Future Improvements
- **Data Cleaning**: Address anomalies (e.g., negative guest counts) and missing ratings.
- **Additional Visualizations**: Add bar charts for guest distribution or time-series analysis for booking trends.
- **Interactive Dashboards**: Convert to a web-based dashboard using Plotly or Streamlit.


