def main():
    
    fileName = []
    contentData = []
    while(True):
        name = input("please enter file name: ")
        
        if name not in fileName:
            fileNo = int(input("how many rows to entry? "))
            i = 0
            outputFile = open(name,"w")
#            contentData = []
            
            while (i < fileNo):
                content = []
                carrier = input("which carrier do you choose? ")
                content.append(carrier)
                weight = float(input("please enter your package weight: "))
                content.append(weight)
                service = input("what is your shipping service? ")            
                content.append(service)    
                print(content)   
                contentData.append(content)
                print(contentData)
                i = i + 1
            fileName.append(name)
            print(fileName)
            
            for row in contentData:
                for r in row:
                    outputFile.write(str(r))
                    outputFile.write(" ")
                outputFile.write("\n")        
            outputFile.close()
                  
        else:
            ans1 = input("Do you want to read the file? ")
            if ans1 == "yes":
                inputFile = open(name,"r")
                inputList = []
                
                for line in inputFile:
                    tempLine = line.strip().split()
                    print(tempLine)
                    inputList.append(tempLine)
                print(inputList)
                inputFile.close()
            
            ans2 = input("Do you want to delete the file? ")
            if ans2 == "yes":
                import os
                os.remove(name)
                main()
            else:
                fileNo2 = int(input("How many rows do you want to add? "))
                print("current file name is "+name)
                outputFile2 = open(name,'a')
                morecontentData = []
                r = 0 
                while (r < fileNo2):
                    morecontent = []
                    carrier = input("which carrier do you choose? ")
                    morecontent.append(carrier)
                    weight = float(input("please enter your package weight: "))
                    morecontent.append(weight)
                    service = input("what is your shipping service? ")            
                    morecontent.append(service)    
                    print(morecontent) 
                    morecontentData.append(morecontent)
                    print(contentData)
                    r = r + 1
                    
                for row2 in morecontentData:
                    for r2 in row2:
                        outputFile2.append(str(r2))
                        outputFile2.append(" ")
                    outputFile2.append("\n")
                outputFile2.close()                
main()                                             
