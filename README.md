# DataScienceMachineLearning
Data Science &amp; Machine Learning class project

# Slide 1 : EVs – Air Quality & Climate Change Impacts 

Hello everyone, and welcome to our presentation we will discuss the link between EVs, air quality and environmental impacts. 

We’ll explore what the data actually says about EVs in Switzerland.  

Are they just a green trend — or do they help us move toward a more sustainable future? 

We have splitted the presentation in 2 parts, first the analysis of Air Quality using mainly No2 as a proxy. Since it has a short lifetime in the atmosphere, it is relevant to analyze it because we can see direct reaction that could be associated with EVs. 

Then we discuss the climate change aspect of EVs with Co2, a gas with a much longer lifetime. 

# Slide 2: EVs in Switzerland 

Let’s start by zooming on Switzerland. 

As you can see on the animation presented, EV’s have gained a lot of popularity recently especially since 2015. 

They are often associated with improved air quality, lower emissions and in general: sustainability.  

But are these claims backed by data? 

In this presentation, we challenge some of these assumptions by analyzing multiple environmental indicators in connection with EV adoption using Machine Learning and Data Science tools. 

#Slide 3: Presentation of our scopes and data 

"To evaluate the impact of EVs, we worked with two spatial levels: national and cantonal.  

At the cantonal level, we focused on pollution, working with PM10 which is a fine particulate matter and a key air pollutant. The scope of our study is the 11 cantons shown in the map. They have different structural characteristics in which we will dive into later. 

At the national level, we extended our scope to include NO₂ and CO₂ along PM10 — giving us both air quality and climate-related insights. 

We included a range of control variables that we thought could influence pollution levels: like GDP, population, air temperature, or precipitation. 

Our main variable of interest is, the share of electric vehicles in the total vehicle fleet. 

This structure allowed us to assess both short-term, local effects and broader, long-term trends." 

 

# Slides 4–5: Inspecting trends on longer timescales & Taking a step back 

"Looking at the long-term trends, things initially seem promising. 

As the share of EVs increases, we notice a decline in NO₂, PM10, and CO₂ emissions. This might lead us to believe that EVs are directly causing this improvement — and that we’re on the right track. 

But then, we take a step back. [NEXT SLIDE] 

We will first focus on air quality and we will analyze the climate change impacts in a later section. 

When we look at this graph: we clearly see that while EVs are indeed increasing, but so are internal combustion engine vehicles. In fact, the total number of vehicles on the road continues to rise. 

This challenges the simplistic belief that EVs are replacing ICEs. What is actually happening is that EVs are being added to an already growing ICE fleet. 

So now the question is: Is the improvement in air quality really driven by EV adoption? Or are there other factors at play? I’ll let Alain explain you what’s happening at a national level. 

# Slide 6: EV and NO₂ – Linear Fit 

To evaluate how well EV share predicts NO₂ levels, we first used a train-test split to build and assess our models. 
To ensure robustness, we also applied K-fold cross-validation, which helps us understand how the model performs across different subsets of the data and guards against overfitting. 

We began with a simple linear regression using EV share as the sole predictor. 

On the test set, the model performed quite well, with an R² of 0.85, meaning it explained 85% of the variance in NO₂ concentrations. 

However, when we looked at the results from 5-fold cross-validation, performance dropped — the average R² fell to 0.37, while the errors increased. 

This drop reveals that the model may struggle to generalize, especially with limited data we have at disposal. 

For these train-test analysis we focus on R² here because it directly reflects how much of the variability in air pollution we can explain with EV share. 

 

# Slide 7: EV and NO₂ – Polynomial Fit, Degree 2 

"We then tested a second-degree polynomial model, to capture non-linear effects. 

The R² score on the test set was 0.44, which doesn’t look impressive at first glance.  

But cross-validation showed more stable performance with an average of 0.51, which is a notable improvement from the linear model. The MAE decreased and the MSE also improved slightly. 

This suggests that a curved relationship may better reflect the real impact of EVs. Perhaps their effect becomes stronger after a critical threshold of adoption." 

# Slide 8: Polynomial Fit – Degree 3 

When have then tried ot increase the degree to 3, this model achieved an impressive R² of 0.92 on the test set and an average R² of 0.82 with the cross validation – the best results so far 

However, it's important to mention a key limitation: with more flexible models like this, we have a high risk of overfitting the data, especially considering the sample we have of 25 years. 

So we think the model is picking up noise rather than true underlying patterns. 

It shows why it is important to rely on domain knowledge and not only statistical results to guide interpretations. 

# Slide 9: Polynomial Fit – Multivariate Linear Regression 

"So far, we looked at how well EV share alone can predict NO₂ levels. But air quality is rarely influenced by a single variable. 

To improve our model — and challenge the idea that EVs are the sole driver — we introduced additional explanatory variables: temperature, log(population), precipitation, and the share of industry in GDP 

Among all of them the industry proxy was quite relevant because industrial activity is a major source of NO₂ emissions. 

The results of this model look really strong. 

On the test set, we achieved an R² of 0.94, with very low MSE and MAE 

Even across 5-fold cross-validation, the model remained stable with an average R² of 0.81. 

So this tells us two things: 

EV share indeed helps explain NO₂ levels. 

But reducing air pollution is clearly a multi-factorial problem. 

# Slide 10: Univariate Regressions – Statmodels 

"To confirm what we saw in the Machine Learnign ANALYSIS we also ran univariate regressions using a statistical modelling package. 

The results were clear: 
Both EV share and industry share in GDP showed statistically significant effects on both NO₂ and PM10 concentrations. 

As you can see, EV share was consistently associated with lower pollution, while a higher industry share was linked with increased pollutant levels." 

# Slide 11: Correlation Table 

We have also looked at correlations between these variables. 

As expected, we see a strong negative correlation between EV share and pollution, and positive one between industrial activity and pollution. 

This also serves as a reminder that: correlation is not causation. 

These patterns are useful to identify signals — but without careful modeling and controls, they could lead to misleading conclusions. 

 

# Slides 15–17: EV – Pollution: Cantonal Models 

Now we’ll try to go beyond national averages and see if our first insights are backed by cantonal observations. We splitted the cantons into 3 different types: Urban, suburban, and rural — based on the location of the air quality measure device. Indeed some devices were positioned at the top of a mountain as it is the case in Lucerne, where the device is at the top of the Rigi. In other places it is positioned in the suburb like the Meyrin’s neighbourhood in Geneva. Or it is located in city centre with dense traffic and population as in Lausanne or Zurich. 

This breakdown helps us understand how local context influences the relationship between EV share and air quality." 

Forme 

Urban Cantons – Slide 15 

We will begin with the urban areas. In urban cantons like Zurich, Vaud, Berne, and Basel-Stadt, the results showed a significant negative effect of EV share on PM10 levels — with a coefficient of -1.34 and high significance. 

That’s what we would expect from dense areas, a lot of people, a lot of vehicles per square kilometer, and probably a higher pollution potential — so EVs have potentially more room to make a difference." 

Suburban Cantons – Slide 16 

"In suburban areas like Geneva and Basel-Landschaft cantons, we still observe a negative coefficient, but this time losing the statistical significance. 

This could be due to less traffic density or differences in local industries, but also due to the limited number of data points in these smaller regions, the correlation might as well be be a spurious correlation. 

These models were trained on only 10 annual observations per canton, so we need to interpret them cautiously. 

FormeRural Cantons – Slide 17 

And finally, let’s observe what’s happening in rural cantons like Lucerne, Neuchâtel, Thurgau, and Valais. We can first notice that, surprisingly, the coefficient turned positive. It suggests that an increase of EV proportion is associated with more pollution. 

This is probably not a causal relationship, it might rather be a reflection of the noise, or again, a side effect of the very small sample size. 

So while the urban findings are insightful and reinforce the positive relationship between EV share and air pollution discovered in the national case, these smaller cantonal models mainly remind us that context and data quantity and quality both matter a lot. 

# Slide 18: Climate Change 

Now let’s shift from local air pollutants like NO₂ and PM10 to a global greenhouse gas: carbon dioxide.  

"To evaluate EVs from a climate perspective, it's essential to understand the difference between emissions-based accounting and consumption-based accounting. 

# Slide 19: EV – Climate Change 

Unlike NO₂, CO₂ has no local boundaries — it mixes in the atmosphere and contributes to climate change regardless of where it's emitted. Lasting 100 years in the atmosphere, the CO2 emission’s source does not matter a lot and analyzing CO₂ emissions within Switzerland only gives us an incomplete picture. 

In fact, Switzerland’s official CO₂ emissions account mostly for territorial production, but miss a major component: consumption-based emissions. In other terms, it corresponds to the emissions embedded in imported goods, services, and of course, vehicles. That means much of the CO₂ linked to an EV’s production — especially from countries with fossil-fuel-heavy industries — isn’t counted in the national emissions at all. 

This is especially relevant when comparing EVs and ICE cars, where the bulk of the emissions comes not just from driving, but from manufacturing and energy production across the full life cycle. 

When we adopt the consumption-based perspective, the climate footprint becomes more transparent — and often, larger than expected, especially in the EV case that does not emit much when utilized 

# Slide 20: EV – Life Cycle Emissions 

"This is where the life cycle assessment of vehicles comes into play. 

For EVs, the manufacturing phase — especially battery production — is much more CO₂-intensive than for traditional cars. 

However, during the use phase, EVs emit far less CO₂ — especially in countries like Switzerland where electricity is low-carbon. 

So the break-even point, or when an EV starts outperforming an ICE in terms of total emissions,  depends on how long the car is used and how clean the energy is. We tried to model it using the international energy agency website, for a medium car-size, 50km/day and a lifespan of 10 years. We see on the left graph that the gap between EV and ICE regarding carbon emissions increases across the time. On the right you see the quantity of co2 equivalents generated to make 1km with 1vehicle. 

So the climate case for EVs might be real — but only if they are part of a broader systemic shift toward fewer cars, longer use, and cleaner grids. Because as mentioned before, we do not replace ICEs by EVs yet. So to achieve Paris Agreement commitments, we might have to drastically reduce the total number of cars, no matter the engine. 

# Slide 21: Conclusion 

As we have seen in this presentation 
The rise of electric vehicles in Switzerland since 2015 has coincided with improvements in air quality — and our models suggest that EV share is a useful predictor of NO₂ levels, especially in urban areas. You can look at the map below that shows how air quality has improved in Paris throughout the years especially driven by the forced reduction in car mobility in the city center. 

However, we also found that other factors — like industrial activity and population growth — play significant roles. 

From a climate perspective, EVs perform better than internal combustion vehicles over their lifetime, but only when used extensively and powered by low-carbon electricity. 

Yet, EVs are often not replacing ICEs — they’re only adding to the overall number of cars. 

Our findings suggest that while EVs can help reduce pollution, they’re not a stand-alone solution. 

 
A more effective path forward is not just replacing ICEs with EVs — but also reducing the total number of cars and taking care of other air pollutant emitters like industry 

Thank you for your attention 
