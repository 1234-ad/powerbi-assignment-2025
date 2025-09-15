# Video Presentation Script Template

## 🎬 5-Minute Video Walkthrough Script

### Opening (30 seconds)
```
"Hello, I'm [Your Name]. Today I'll walk you through my Power BI dashboard 
analyzing employee performance and returns with year-over-year comparisons 
for the 2025 assignment.

This dashboard provides insights into return rates, employee performance, 
and key trends that can help drive business decisions. Let me start by 
showing you the data model foundation."
```

### Data Model Overview (1 minute)
```
"First, let me show you the data model structure. [Switch to Model View]

As you can see, I've implemented a star schema design with:
- A central Date dimension table that I created using DAX
- People as our employee dimension
- Orders and Returns as our fact tables
- All connected with proper one-to-many relationships

The Date table is marked as the official date table, which enables our 
time intelligence calculations. Notice how both Orders and Returns connect 
to the Date table through their respective date fields, and both connect 
to People through Employee_ID.

This structure allows for efficient cross-filtering and supports our 
year-over-year analysis requirements."
```

### DAX Measures Demonstration (2 minutes)
```
"Now let me demonstrate the key DAX measures. [Switch to Report View]

Starting with our core metrics:

1. Return Rate Percentage: This calculates the number of returns divided 
   by total transactions. You can see it's currently at [X]%.

2. For year-over-year analysis, I'm using SAMEPERIODLASTYEAR function. 
   Watch as I show the YoY change - [point to indicator] - this shows 
   we're [up/down] [X]% compared to last year.

3. Average Return Value: Currently at $[X], with a YoY change of [X]%.

4. The Top 5 Employees ranking is dynamic - it automatically updates 
   based on return counts. Notice how [Employee Name] leads with [X] 
   returns, showing a [increase/decrease] from last year.

5. Monthly trends: This line chart shows our return patterns over time, 
   with the blue line representing current year and the orange line 
   showing previous year for comparison.

All these calculations handle missing data gracefully and provide 
meaningful business insights."
```

### Dashboard Navigation (1.5 minutes)
```
"Let me walk you through the dashboard interactivity. [Navigate dashboard]

The dashboard is organized into clear sections:
- KPI cards at the top showing our key metrics with YoY indicators
- Charts below providing detailed analysis

Watch the cross-filtering in action: [Click on employee slicer]
When I select a specific employee, all visuals update automatically. 
The return rate, trends, and contribution percentages all filter 
to show just that employee's data.

[Reset filters] Now let me show the regional analysis: [Use region slicer]
This allows stakeholders to drill down into specific geographic areas.

The date slicer enables time-based analysis: [Demonstrate date filtering]
You can focus on specific periods while maintaining YoY comparisons.

Notice the consistent color scheme and professional layout - I've used 
a corporate blue theme with clear visual hierarchy. Each chart has 
descriptive titles and proper formatting for business presentation."
```

### Key Insights & Conclusion (1 minute)
```
"Based on this analysis, here are the key insights:

1. Overall return rate has [increased/decreased] by [X]% year-over-year, 
   indicating [positive/concerning] trends in product quality or customer 
   satisfaction.

2. [Employee Name] consistently shows the highest return volume, which 
   may indicate either high sales volume or potential training needs.

3. Seasonally, we see [pattern description] - this suggests [business insight].

4. The average return value trend shows [insight], which impacts our 
   bottom line by approximately $[amount] annually.

These insights enable data-driven decisions around employee training, 
product quality improvements, and customer service enhancements.

The dashboard provides stakeholders with real-time visibility into 
performance trends and supports strategic planning through historical 
comparisons.

Thank you for watching. The complete PBIX file and this presentation 
are submitted via the Google Form as requested."
```

## 🎯 Delivery Tips

### Before Recording:
- [ ] **Practice 2-3 times** to ensure smooth delivery
- [ ] **Test screen recording** software and audio
- [ ] **Close unnecessary applications** for clean screen
- [ ] **Prepare backup talking points** in case of technical issues

### During Recording:
- [ ] **Speak clearly** and at moderate pace
- [ ] **Use cursor** to highlight specific elements
- [ ] **Pause briefly** between sections
- [ ] **Stay within 5-minute limit**

### Technical Setup:
```
Recommended Settings:
- Resolution: 1920x1080 (1080p)
- Frame Rate: 30 fps
- Audio: Clear microphone, no background noise
- Software: OBS Studio, Camtasia, or built-in screen recorder
```

## 📝 Customization Notes

### Adapt This Script:
1. **Replace [Your Name]** with your actual name
2. **Fill in actual values** for metrics (X%, $X, etc.)
3. **Customize insights** based on your specific data
4. **Adjust timing** based on your speaking pace
5. **Add personal touches** while maintaining professionalism

### Key Points to Emphasize:
- **Technical competency**: Show you understand DAX and data modeling
- **Business acumen**: Connect technical features to business value
- **Attention to detail**: Highlight professional design choices
- **Problem-solving**: Explain how the dashboard addresses requirements

### Common Mistakes to Avoid:
- **Reading directly from script** (sound natural)
- **Going over time limit** (practice with timer)
- **Technical jargon overload** (explain for business audience)
- **Forgetting to show YoY comparisons** (key requirement)
- **Poor audio quality** (test beforehand)

## 🎬 Alternative Shorter Version (3 minutes)

If you need a condensed version:

### Quick Script:
```
"Hello, I'm [Name]. This Power BI dashboard analyzes employee returns 
with year-over-year comparisons.

[30 sec] Data model: Star schema with Date, People, Orders, and Returns 
tables, enabling time intelligence calculations.

[90 sec] Key features: Return rate tracking, YoY comparisons using 
SAMEPERIODLASTYEAR, dynamic Top 5 rankings, and interactive filtering.

[60 sec] Business insights: [2-3 key findings with specific numbers]

The dashboard provides actionable insights for improving employee 
performance and reducing return rates. Thank you."
```

Remember: **Confidence and clarity matter more than perfect memorization!**