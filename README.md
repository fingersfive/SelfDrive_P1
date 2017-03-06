# SelfDrive_P1

## General approach was to find all lines on either side, and then using gradient to extend each to the full extent (bottom to horizon), and then to take the average x value at the bottom and the average x value at the top to get the manin line.

            # find x when y at full extent - point 1 = (x, imshape[0])
            x_bottom = int((imshape[0] - intercept)/gradient)

            # find x when y at perspective limit - point 1 = (x, 390)
            x_middle = int((350 - intercept)/gradient)

## Found was getting some lines with zero gradient (horizontal) hence the following (this probably due to other settings?) 
if gradient == 0:
     continue
     
## Also found some extended lines with strange gradient, therefore limited with following code - probably the reason the lines are flashing
            if gradient > 0.5 and gradient < 0.85:    
                x_bottom_left_total += x_bottom
                x_middle_left_total += x_middle
                left_side_counter += 1 
            elif gradient < -0.5 and gradient > -0.85:
                x_bottom_right_total += x_bottom
                x_middle_right_total += x_middle
                right_side_counter += 1
                
## Use global values to try and get smoothing by getting average of last two lines

