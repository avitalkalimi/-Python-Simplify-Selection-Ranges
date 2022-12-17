# Simplify-Selection-Ranges
You are given an array of numbers and must simplify the array by replacing ranges of 3 or more items with the shorthand #-# equivalent and returning the result as a string, sorted from lowest to highest

def sidor(str_source):

    str_source = str_source[1:-1]
    source = str_source.split(",")
    source = [int(c) for c in source ]

    source.sort()
    print(source)
    sfiga = []
    mahrozet = ""

    for i in range(len(source)):
        if len(mahrozet) == 0:  # first one
            if i == len(source) - 1: # the last one
                if source[i] == sfiga[-1]+1: # if Increase
                    sfiga.append(source[i])
                    if len(sfiga) > 2:
                        mahrozet += str(sfiga[0])
                        mahrozet += "-"
                        mahrozet += str(sfiga[-1])
                    else:
                        mahrozet += str(sfiga[0])
                        mahrozet += ","
                        mahrozet += str(sfiga[1])
                else:
                   mahrozet += str(source[i])
            elif source[i] + 1 == source[i + 1]: # if Increase
                sfiga.append(source[i])
            else:
                if source[i] == sfiga[-1] + 1:
                    sfiga.append(source[i])
                if len(sfiga) > 2:
                   mahrozet += str(sfiga[0])
                   mahrozet += "-"
                   mahrozet += str(sfiga[-1])
                   sfiga = []
                else:
                   mahrozet += str(sfiga[0])
                   mahrozet += ","
                   mahrozet += str(sfiga[1])
                   sfiga = []

        elif i == len(source) - 1:  # last one
            if len(sfiga) > 2:
                if source[i] == sfiga[-1] + 1:
                    sfiga.append(source[i])
                    mahrozet += ","
                    mahrozet += str(sfiga[0])
                    mahrozet += "-"
                    mahrozet += str(sfiga[-1])
                else:
                    mahrozet += ","
                    mahrozet += str(sfiga[0])
                    mahrozet += "-"
                    mahrozet += str(sfiga[-1])
                    mahrozet += ","
                    mahrozet += str(source[i])
            else:
                mahrozet += ","
                mahrozet += str(source[i])

        elif source[i] + 1 == source[i + 1]:  # yes alia
            sfiga.append(source[i])

        else:  # ein alia
            if len(sfiga) > 0:
                if source[i] == sfiga[-1] + 1:
                    sfiga.append(source[i])
                if len(sfiga) > 2:
                    mahrozet += ","
                    mahrozet += str(sfiga[0])
                    mahrozet += "-"
                    mahrozet += str(sfiga[-1])
                    sfiga = []
                else:
                    mahrozet += ","
                    mahrozet += str(sfiga[0])
                    mahrozet += ","
                    mahrozet += str(sfiga[1])
                    sfiga = []

            elif len(sfiga) > 2:
                mahrozet += ","
                mahrozet += str(sfiga[0])
                mahrozet += "-"
                mahrozet += str(sfiga[-1])
                mahrozet += ","
                mahrozet += str(source[i])
                sfiga = []

            else:
                for i in sfiga:
                    mahrozet += "," + str(sfiga[i])
                mahrozet += ","
                mahrozet += str(source[i])
                sfiga = []

    return mahrozet
