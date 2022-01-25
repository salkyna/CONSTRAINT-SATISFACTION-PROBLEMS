import pandas as pd
import csv
import plotly.express as px

# Do not modify the line below.
# Define the variables
countries = ["Argentina", "Bolivia", "Brazil", "Chile", "Colombia", "Ecuador", "Falkland Islands", "Guyana", "Paraguay",
             "Peru", "Suriname", "Uruguay", "Venezuela"]

# Do not modify the line below.
# Define the domain
colors = ["blue", "green", "red", "yellow"]

# Write your code here
no_neighbour = ['NONE']


class my_dictionary(dict):

    # __init__ function
    def __init__(self):
        self = dict()

    def add(self, key, value):
        self[key] = value

#Create an empty dictionary object
dictionary = my_dictionary()

# Function to read neigbours of each country and populate the empty dictionary created above
def read_neighbors(myDictionary):
    with open("table.csv", "r", encoding="utf-8") as t:
        next(t)
        reader = csv.reader(t)

        for row in reader:
            country = row[0]
            neighbours = row[1:len(row)]
            myDictionary.add(country, neighbours)
    return myDictionary

# Check if there are countries having no neighbours and return True as an output
def map_check(color_map, country, adjacency_dict):
    if dictionary[country] == no_neighbour:
        return True
    for neighbour in dictionary[country]:
        if color_map[neighbour] == color_map[country]:
            return False
    return True

# Do backtracking 
def backtracking(items_list, dict_items_to_vals, index,
                         set_of_assignments, legal_assignment_func, *args):
    # recursion 
    if all(value in set_of_assignments for value in
           dict_items_to_vals.values()):
        return True
    else:
        # going over every possible value
        for value in set_of_assignments:
            item_check = items_list[index]
            temporary = dict_items_to_vals[item_check]
            # assigning the value
            dict_items_to_vals[item_check] = value
            if legal_assignment_func(dict_items_to_vals, item_check, args):
                # recursion in case action s legal
                if backtracking(items_list, dict_items_to_vals,
                                        index + 1, set_of_assignments,
                                        legal_assignment_func, *args):
                    return True
            # going one step back in case we have reached a dead-end
            dict_items_to_vals[item_check] = temporary
        return False

# Color the map
def map_coloring(num_colors=4):
    color_map = dict(dictionary)
    items_list = list(dictionary.keys())
    set_of_assignments = colors[:num_colors]
    legal_assignment_func = map_check
    if backtracking(items_list, color_map, 0,
                            set_of_assignments, legal_assignment_func,
                            dictionary):
        return color_map
    else:
        return None

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
    # Creating dictionary
    read_neighbors(dictionary)
    # Creating colormap
    colormap = map_coloring()

print("Map checking:", map_check(map_coloring(), 'Argentina', dictionary))

print("Map Colored:\n", map_coloring())

print("Dictionary:\n", read_neighbors(dictionary))

plot_choropleth(colormap)
