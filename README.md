# LWFA_database

If followed by NULL, then optional.

User Database:
(Required)
user_id INTEGER,
user_name TEXT NOT NULL,
institution TEXT,
contact_email TEXT

---------------------------------------------------------------------------------------------------------------------------------------

external Link where you store your experiment or simulation data:
simulation_id INTEGER NULL,                        #Simulation ID you give
experiment_id INTEGER NULL,                        #Experiment ID you give
input_filename TEXT NULL,                          #File you store the 
output_filename TEXT NULL,
output_file_path TEXT NULL,                        #output directory of your experiment/simulation output file
file_URL TEXT NULL,                                #URL if the output data is online
paper_ref_URL TEXT NULL,                           #URL if paper published

---------------------------------------------------------------------------------------------------------------------------------------

Simulation primary database: 
user_id INTEGER,                                    
simulation_name TEXT,
creation_date DATE NULL,
simulation_software TEXT,                         #Software used for simulation
simulation_dimension TEXT,                        #1D,2D, Cylinderical or 3D
simulation_purpose TEXT,                          #Purpose of simulation
injection BOOL,                                   #If there's any particles injected
injection_type TEXT,                              #self injection (SF), ionization injection(ION), self modulated(SM), down ramp(DR),etc
                                                  #Please only fill in the capitalized initials
plasma BOOL,                                      #If there's plasma
plasma_species TEXT,
laser BOOL,
accelerated_particle BOOL,                        #If there are particles being accelerated        
accelerated_particle_charge FLOAT,                
external_injection BOOL,                          #If external injection method

---------------------------------------------------------------------------------------------------------------------------------------

Simulation input parameters:
input_id INTEGER PRIMARY KEY,
simulation_id INTEGER,
dist FLOAT,
--simulation box parameters
XMax FLOAT,
YMax FLOAT NULL,
ZMax FLOAT NULL,
Nx INTEGER,
Ny INTEGER NULL,
Nz INTEGER NULL,
dx FLOAT,
dy FLOAT NULL,
dz FLOAT NULL,
microparticles_per_cell INT NULL,
-- boosted frame specific parameters
boost BOOL,
boost_gamma FLOAT NULL,
-- plasma specific parameters 
plasma_density FLOAT NULL,
density_ramp BOOL NULL,
density_ramp_shape TEXT NULL,
-- Laser specific parameters
Laser_shape TEXT NULL,
Frequency FLOAT NULL,
Laser_energy FLOAT NULL,
tau_FWHM FLOAT NULL,
a0 FLOAT NULL,
w0 FLOAT NULL,
-- External Injection specific parameters
charge FLOAT NULL,
shape TEXT NULL,
init_emit FLOAT NULL

---------------------------------------------------------------------------------------------------------------------------------------

Experiment Primary Database: 
experiment_id INTEGER PRIMARY KEY,
user_id INTEGER,
experiment_name TEXT,                                  
experiment_date DATE,
facility TEXT,                                    #Experiment Facility
experiment_purpose TEXT NULL,                     #Experiment Purpose
injection BOOL,                                   #If injection
injection_type TEXT,
plasma BOOL,                                      #If there's plasma involved
plasma_species TEXT,          
laser BOOL,                                       #If Laser is used   
laser_type TEXT NULL,                             #type of laser used
laser_specific TEXT NULL,                         #Other details of the laser facility
accelerated_particle BOOL,                        #If there's accelerated particle

---------------------------------------------------------------------------------------------------------------------------------------

Experiment Input Database:
input_id INTEGER PRIMARY KEY,
experiment_id INTEGER,
dist FLOAT,                                       #distance of LWFA propagation
-- plasma specific parameters 
plasma_density FLOAT NULL,                        #Plasma density                       
density_ramp_shape TEXT NULL,
gas_jet TEXT NULL,                                #Specifics of the gas jet
-- Laser specific parameters
Laser_shape TEXT NULL,                            #Laser configuration
Frequency FLOAT NULL,                             #Laser frequency
Laser_energy FLOAT NULL,                          #Laser Energy in J
tau_FWHM FLOAT NULL,                              #Laser pulse duration in ps
a0 FLOAT NULL,                              
w0 FLOAT NULL,                                    #Laser waist in um

---------------------------------------------------------------------------------------------------------------------------------------

