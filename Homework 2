# ===========================
# Student Name: Seong Hyeon Yoon
# Student ID: 116392723
# ===========================

# Implement the functions according to the exercises listed in the homework.
# Use the main() function to test your code.

# Exercise 1: Decimation
def decimation(point_cloud, compression_factor):
    d = round(1 / compression_factor)
    if d - int(d) >= 0.5:
        d = int(d) + 1
    else:
        d = int(d)

    new_lst = []

    for i in range(0, len(point_cloud), d):
        new_lst.append(point_cloud[i])
    return new_lst

# Exercise 2: Scaling
def scale_point_cloud(decimated_pts_cloud, scaling_factor):
    for i in range(len(decimated_pts_cloud)):
        for j in range(len(decimated_pts_cloud[i])):
            decimated_pts_cloud[i][j] *= 2

    return decimated_pts_cloud
        
# Exercise 3: Checking Rotation Matrix Orthogonality
def check_orthogonality(R):
    r = 0
    c = 0
    lst = []
    for i in range(len(R)):
        for j in range(len(R[i])):
            r += (R[i][j])**2
        mrow = r**0.5
        r = 0
        if 1 - 1e-6 <= mrow <= 1 + 1e-6:
            lst.append(True)
        else:
            lst.append(False)

    for j in range(len(R[i])):
        for i in range(len(R)):
            c += (R[i][j])**2
        mcolumn = c**0.5
        c = 0
        if 1 - 1e-6 <= mcolumn <= 1 + 1e-6:
            lst.append(True)
        else:
            lst.append(False)

    if lst.count(False) >= 1:
        return False
    else:
        return True
        
        
# Exercise 4: Rotating a 3D Point
def rotate_3d_point(P, R):
    r = 0
    P2 = []
    if check_orthogonality(R):
        for i in range(len(R)):
            for j in range(len(R[i])):
                r += R[i][j]*P[j]
            P2.append(r)
        return P2
    else:
        return "invalid value"

# Exercise 5: Translating a 3D Point
def translate_3d_point(P, t):
    P2 = []
    for i in range(len(P)):
        P2.append(P[i]+t[i])
    return P2

# Exercise 6: Transforming a 3D Point Cloud
def transform_point_cloud(P, R, t):
    P2 = []
    for i in range(len(P)):
        RP = rotate_3d_point(P[i], R)
        P2.append(translate_3d_point(RP, t))
    return P2

# Exercise 7: Calculating Distance Between Two Point Clouds
def point_cloud_dist(point_cloud, trans_pt_cloud):
    x = 0
    dist = []
    for i in range(len(point_cloud)):
        for j in range(len(point_cloud[i])):
            x += (point_cloud[i][j] - trans_pt_cloud[i][j])**2
        dist.append(x**0.5)
    return dist

# Exercise 8: Finding Points Inside a Sphere
def find_points_in_sphere(point_cloud, sph_center, sph_radius):
    r = 0
    lst = []
    for i in range(len(point_cloud)):
        for j in range(len(point_cloud[i])):
            dist = ((point_cloud[i][j] - sph_center[j])**2)**0.5
            if dist <= sph_radius:
                lst.append(dist)
    return lst

# ====================================
# Use this to test your implementation
# ====================================
def main():
    # Example point cloud (20 points in 3D space)
    point_cloud = [
        [0.78, 6.49, 0.07], [4.47, 9.34, 8.23], [5.16, 6.29, 3.75],
        [4.29, 9.54, 2.02], [3.73, 3.8, 3.57], [2.27, 1.63, 1.43],
        [7.16, 2.89, 3.98], [1.85, 3.19, 7.93], [9.79, 7.89, 0.86],
        [5.07, 4.52, 8.21], [7.39, 7.38, 5.37], [2.09, 0.42, 7.81],
        [8.78, 4.93, 4.54], [6.15, 3.47, 2.9], [8.04, 3.28, 0.64],
        [1.04, 7.99, 1.43], [1.52, 9.68, 6.94], [1.84, 3.98, 1.85],
        [2.44, 7.71, 8.55], [6.44, 7.72, 8.83]
    ]
    
    # Test Exercise 1: Decimation
    print("\nTesting Exercise 1: Decimation")
    decimated_pts_cloud = decimation(point_cloud, 0.5)
    print("Decimated Point Cloud:", decimated_pts_cloud)
    
    # Test Exercise 2: Scaling
    print("\nTesting Exercise 2: Scaling")
    scaled_pts_cloud = scale_point_cloud(decimated_pts_cloud, 2)
    print("Scaled Point Cloud:", scaled_pts_cloud)
    
    # Test Exercise 3: Checking Orthogonality
    print("\nTesting Exercise 3: Checking Orthogonality")
    R = [
        [-0.1650948, 0.8194394, -0.5488741],
        [-0.9797467, -0.2001973, -0.0041876],
        [-0.1133146, 0.5370662, 0.8358946]
    ]
    print("Is Orthogonal?", check_orthogonality(R))
    
    # Test Exercise 4: Rotating a 3D Point
    print("\nTesting Exercise 4: Rotating a 3D Point")
    print("Rotated Point:", rotate_3d_point(point_cloud[0], R))
    
    # Test Exercise 5: Translating a 3D Point
    print("\nTesting Exercise 5: Translating a 3D Point")
    t = [1, -0.5, 2]
    print("Translated Point:", translate_3d_point(point_cloud[0], t))
    
    # Test Exercise 6: Transforming the entire Point Cloud
    print("\nTesting Exercise 6: Transforming the Point Cloud")
    trans_pt_cloud = transform_point_cloud(point_cloud, R, t)
    print("Transformed Point Cloud:", trans_pt_cloud)
    
    # Test Exercise 7: Distance Between Two Point Clouds
    print("\nTesting Exercise 7: Distance Between Two Point Clouds")
    print("Average Distance Between Clouds:", point_cloud_dist(point_cloud, trans_pt_cloud))
    
    # Test Exercise 8: Finding Points Inside a Sphere
    print("\nTesting Exercise 8: Finding Points Inside a Sphere")
    sph_center = [4, 8, 2]
    sph_radius = 3
    print("Points Inside Sphere:", find_points_in_sphere(point_cloud, sph_center, sph_radius))
    
# Standard Python construct to run the code only if this file is executed directly
if __name__ == "__main__":
    main()
