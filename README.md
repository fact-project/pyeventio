# coming soon #

I have no idea, why this all renders so ugly

# install with #
    
    pip install git+https://bitbucket.org/dneise/fact_shift_helper#egg=fact_shift_helper

# Example #

If you like to plot the origin of the Cherenkov photons of the first shower in file `data/telescope.dat` you can do:


    import matplotlib.pyplot as plt
    from mpl_toolkits.mplot3d import Axes3D

    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')

    import eventio
    f = eventio.EventIoFile('data/telescope.dat')
    b = f.next().bunches

    cz = 1 - (b['cx']**2 + b['cy']**2)

    x = b['x'] + (b['zem'] / cz)*b['cx']
    y = b['y'] + (b['zem'] / cz)*b['cy']

    ax.plot(x/100., y/100., b['zem']/1e5, 'o')
    ax.set_xlabel('Xaxis [m]')
    ax.set_ylabel('Yaxis [m]')
    ax.set_zlabel('Zaxis [km]')
    plt.show()


It might look similar to this picture.

https://bitbucket.org/repo/ddng5E/images/4235100275-a_shower.png