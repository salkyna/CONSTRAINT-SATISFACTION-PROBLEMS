
from simpleai.search import CspProblem, backtrack
import plotly.express as px

#We define the function that imposes the constraint that neighbors should be different
def constraint_function(countries, values):
    return values [0] != values [1]


countries = ("Argentina", "Bolivia", "Brazil", "Chile", "Colombia", "Ecuador", "Falkland Islands", "Guyana", "Paraguay", "Peru", "Suriname", "Uruguay", "Venezuela")

colors = dict ((country, ['blue', 'green', 'red', 'yellow']) for country in countries)

#We convert the map information into sth that algorithm can understand.
#We pair the adjacent countries and apply constraint_function to each pair
constraints = [(("Argentina", "Bolivia"), constraint_function),
			   (("Argentina", "Brazil"), constraint_function),
			   (("Argentina", "Chile"), constraint_function),
			   (("Argentina", "Peru"), constraint_function), 
			   (("Argentina", "Uruguay"), constraint_function),
			   (("Bolivia", "Brazil"), constraint_function),
			   (("Bolivia", "Chile"), constraint_function),
			   (("Bolivia", "Paraguay"), constraint_function),
			   (("Bolivia", "Peru"), constraint_function),
			   (("Brazil", "Colombia"), constraint_function),
			   (("Brazil", "Guyana"), constraint_function),
			   (("Brazil", "Paraguay"), constraint_function),
			   (("Brazil", "Peru"), constraint_function),
			   (("Brazil", "Suriname"), constraint_function),
			   (("Brazil", "Uruguay"), constraint_function),
			   (("Brazil", "Venezuela"), constraint_function),
			   (("Chile", "Peru"), constraint_function),
			   (("Colombia", "Ecuador"), constraint_function),
			   (("Colombia", "Peru"), constraint_function),
			   (("Colombia", "Venezuela"), constraint_function),
			   (("Ecuador", "Peru"), constraint_function),
			   (("Guyana", "Suriname"), constraint_function),
			   (("Guyana", "Venezuela"), constraint_function)]

#We initialize the object by using variables and constraints
problem = CspProblem (countries, colors, constraints)

#Solve the problem and print the solution
output = backtrack (problem)

print (output)

for k, v in output.items():
    print (k, '==>', v)


# Do not modify this method, only call it with an appropriate argument.
# colormap should be a dictionary having countries as keys and colors as values.
def plot_choropleth(colormap):
    fig = px.choropleth(locationmode="country names",
                        locations=countries,
                        color=countries,
                        color_discrete_sequence=[colormap[c] for c in countries],
                        scope="south america")
    fig.show()

# Implement main to call necessary functions
if __name__ == "__main__":

    # coloring test
    colormap_test = output

    plot_choropleth(colormap=colormap_test)




