colors = ['Red', 'Blue', 'Green']
states = ['wa', 'nt', 'sa', 'q', 'nsw', 'v']
neighbors = {}
neighbors['wa'] = ['nt', 'sa']
neighbors['nt'] = ['wa', 'sa', 'q']
neighbors['sa'] = ['wa', 'nt', 'q', 'nsw', 'v']
neighbors['q'] = ['nt', 'sa', 'snw']
neighbors['nsw'] = ['q', 'sa', 'v']
neighbors['v'] = ['sa', 'nsw']

colors_of_states = {}

def promising(state, color):
    for neighbor in neighbors.get(state):
        color_of_neighbor = colors_of_states.get(neighbor)
        if color_of_neighbor == color:
            return False
    return True
    
def get_color_for_state(state):
    for color in colors:
        if promising(state, color):
            return color
        
def main():
    for state in states:
        colors_of_states[state] = get_color_for_state(state)
    print("\n",colors_of_states,"\n")
        
if __name__ == "__main__":
    main()
