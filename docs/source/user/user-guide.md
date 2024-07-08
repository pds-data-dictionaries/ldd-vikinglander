PDS4 Viking Lander Mission Dictionary User's Guide  
2024-07-08 
Jennifer Ward

> Note to authors who use this outline: The outline is a
> suggestion only. It includes the minimum of content needed to inform the
> dictionary user. Authors are expected to tailor the outline to their particular
> purposes, elaborating and providing context as needed.

# Introduction
   1. Purpose of this User's Guide
   - This User's Guide provides an overview of the Viking Lander Mission Data Dictionary. It details how to include the dictionary in a PDS4 label, describes the organization of classes and attributes, provides definitions of the classes and attributes, and lists examples of labels that use it.
   2. Audience
   - This User's Guide should be useful to data providers intending to archive Viking Lander data with PDS as well as PDS Nodes who are working with these data providers.

# Overview of the Viking Lander Mission Data Dictionary

The Viking Lander Mission Data Dictionary contains classes and attributes specific to the Viking Lander mission and its instruments. 
Steward: Jennifer Ward, PDS Geosciences Node, geosci@wunder.wustl.edu

# How to Include the Viking Lander Mission Data Dictionary in a PDS4 Label

The dictionary consists of a set of files with names in the form PDS4_VIKINGLANDER_xxxx_yyyy.ext, where
- xxxx = the PDS4 Information Model version, e.g. 1L00 
- yyyy = the Viking Lander Mission Dictionary version, e.g. 1000

and the file extensions are

- .csv = A comma-separated value table of dictionary attributes 
- .JSON = The dictionary contents in JSON format 
- .sch = The dictionary "rules" as an XML Schematron file 
- .txt = The report generated when the dictionary was built 
- .xml = The PDS4 label that describes this set of files 
- .xsd = The dictionary contents as an XML schema file

Only the schema and Schematron files are needed for validating a PDS4 label.

The latest version of this dictionary may be found on the PDS web site at https://pds.nasa.gov/datastandards/dictionaries/index-missions.shtml#vikinglander.

The following is an example showing the use of this dictionary in a PDS4 label.

```
   <?xml version="1.0" encoding="UTF-8"?>
   <?xml-model href="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1L00.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
   <?xml-model href="https://pds.nasa.gov/pds4/mission/mgn/v1/PDS4_VIKINGLANDER_1L00_1000.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>    
   <Product_Observational xmlns="http://pds.nasa.gov/pds4/pds/v1"
       xmlns:mgn="http://pds.nasa.gov/pds4/mission/vikinglander/v1"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://pds.nasa.gov/pds4/pds/v1                    https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1L00.xsd
                           http://pds.nasa.gov/pds4/mission/vikinglander/v1   https://pds.nasa.gov/pds4/mission/mgn/v1/PDS4_VIKINGLANDER_1L00_1000.xsd">
```

The following is an example showing the location of the Viking Lander dictionary classes and attributes in a PDS4 label.

```
<Observation_Area>
    ...
    <Mission_Area>
      <vikinglander:Viking_Lander_Parameters>
        <vikinglander:Observation_Information>  </>
          <vikinglander:product_type_name> </>
          <vikinglander:mission_phase_name> </>
          [ <vikinglander:sol_number>  </> ]
          OR 
          [ <vikinglander:start_sol_number>  </>
            <vikinglander:stop_sol_number> </> ]
          <vikinglander:native_time> </>
          <vikinglander:local_hour> </>
          <vikinglander:observation_name> </>
       </vikinglander:Observation_Information> </>
       <vikinglander:Image_Parameters>
               diode_name
               start_scan_azimuth
               stop_scan_azimuth
               mirror_center_elevation
               sampling_interval
               offset_number
               gain_number
               psa_temperature
               scan_rate
               start_rescan_sample
               total_rescan_samples
               missing_scans
               data_path_type
               dust_flag          
       </vikinglander:Image_Parameters>   
    </vikinglander:Viking_Lander_Parameters>
  </Mission_Area>    
         ...         
```

The namespace for the Viking Lander Mission Dictionary is http://pds.nasa.gov/pds4/mission/vikinglander/v1, abbreviated "vikinglander:".

# Organization of Classes and Attributes

See the [schematic](../../VIKIGNLANDER_LDD_diagram.png) for a visual representation of the classes and attributes (not yet available).

Below is a list showing the hierarchy of classes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

- Viking_Lander_Parameters class
    - Observation_Information class
    - Image_Parameters class

Below are lists showing the hierarchy of class attributes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

## Viking_Lander_Parameters Class
- Observation_Information class
- Image_Parameters class

## Observation_Information Class
- product_type_name
- mission_phase_name
{
- sol_number
}
- OR
{
- start_sol_number
- stop_sol_number
}
- native_time
- local_hour
- observation_name

## Image_Parameters Class
- diode_name
- start_scan_azimuth
- stop_scan_azimuth
- mirror_center_elevation
- sampling_interval
- offset_number
- gain_number
- psa_temperature
- scan_rate
- start_rescan_sample
- total_rescan_samples
- missing_scans
- data_path_type
- dust_flag

# Definitions

Classes (in alphabetical order)

*Image_Parameters*
- This class provides a set of parameters that describe a Viking Lander image.
- Minimum occurrences: 0
- Maximum occurrences: 1

*Observation_Information*
- The Observation_Information class provides information about a Viking Lander science observation.
- Minimum occurrences: 1
- Maximum occurrences: 1

*Viking_Lander_Parameters*
- The Viking_Lander_Parameters class is a superclass containing all Viking Lander mission classes.
- Minimum occurrences: 1
- Maximum occurrences: 1

Attributes (in alphabetical order)

*diode_name*
Name for one of the twelve photodiode in a VL camera.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - bb1 - One of four broadband high-resolution diodes. BB1 had the shortest
          in focus distance. It was used for imaging close to the lander.
  - bb2 - One of four broadband high-resolution diodes. BB2 had an intermediate
          in focus distance.
  - bb3 - One of four broadband high-resolution diodes. BB3 had an intermediate
          in focus distance.
  - bb4 - One of four broadband high-resolution diodes. BB4 had the longest
          in focus distance. It was used for imaging objects further from the lander.
  - survey - A broadband low-resolution diode. The Survey diode was used
          to take images that covered a large area at low resolution.
  - blue - A low-resolution diode with a passband centered at blue wavelengths.
  - green - A low-resolution diode with a passband centered at green wavelengths.
  - red - A low-resolution diode with a passband centered at red wavelengths.
  - ir1 - One of three low-resolution diodes with a passband centered at Infrared wavelengths.
  - ir2 - One of three low-resolution diodes with a passband centered at Infrared wavelengths.
  - ir3 - One of three low-resolution diodes with a passband centered at Infrared wavelengths.
  - sun - A broadband high-resolution diode with a filter designed for
          imaging the Sun without saturating the DN range.
  - undefined - This value indicates a calibration sequence was collected using
          all the diodes.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*downlink_path*
The data transmission path from the cameras to Earth. The path could be recorded for later transmission or 
transmitted in realtime as the camera scanned. The data could be sent either by a UHF link to an orbiter or 
S-band link directly to Earth.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - recorded_uhf_link - Image recorded to Lander tape and transmitted by UHF relay to Earth.
  - recorded_s-band_link - Image recorded to Lander tape and transmitted directly to Earth on S-Band link.
  - realtime_uhf_link - Image transmitted by UHF relay to Earth while being acquired.
  - realtime_s-band_link - Image transmitted direcly to Earth on S-Band link while being acquired.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*dust_flag*
A flag indicating whether a dust sequence was done with an image.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - true - A dust sequence was done.
  - false - No dust sequence was done.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*gain_number*
One of six gain settings used in the conversion of photodiode voltage to DN.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 5

*local_hour*
The hour and fraction hour within a sol that an observation began assuming a sol has 24 hours.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0.0
- Maximum value: 24.0

*mirror_center_elevation*
The commanded center elevation of the scanning mirror used for an image. Zero elevation is generally pointed 
toward the horizon with negative values below and positive values above. Note that actual center elevation may 
be different for some non-nominal imaging modes.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: -60.0
- Maximum value: 40.0
- Unit of measure type: Units_of_Angle
- Unit id: degree

*mission_phase_name*
The mission_phase_name identifies a time period within the mission.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - Primary_Mission - The Viking Lander 1 spacecraft separated from the VO1 orbiter and
          descended to the Martian surface on July 20, 1976. The Viking Lander 2 spacecraft
          separated from the VO2 orbiter and descended to the Martian surface on
          September 3, 1976. The Primary Mission
          ended at the start of the solar conjunction in November 15, 1976.
  - Extended_Mission - The Viking Extended Mission began after solar conjunction. The
          two lander spacecraft analyzed additional soil samples and dug three
          deep holes in the surface. All four spacecraft monitored the planet
          through the cycle of seasons. During the winter season, the landers
          operated in an automatic manner designed to allow the spacecraft to
          survive the cold temperatures and still return some data. Dates: 1976-11-15
          to 1978-05-31.
  - Continuation_Mission - Lander activities consisted of measurements by the imaging,
          meteorology, and XRFS instruments operating in a fully automated manner.
          Dates: 1978-05-31 to 1979-02-26.
  - Interim_Period - The Interim Period mission phase occurred during the time of the Voyager
          2 encounter with Jupiter. Thus, communications to and from the Viking
          spacecraft were limited. The landers continued to operate in an
          automated manner making imaging and meteorology observations. A final
          VL2 surface sampler sequence was conducted during this mission phase as
          an engineering test in the cold temperatures of mid winter.
          Dates: 1979-02-26 to 1979-07-19.
  - Survey_Mission - The plan for the landers was to collect image and
          meteorology data for as long as possible. Because VL2 no longer had a
          direct downlink capability, it meant that VL2 could return data only
          as long as VO1 provided a relay link, once every seven weeks.
          Communications with VL2 ended on April 11, 1980 after its batteries
          could no longer hold a charge. VL2 operated on the surface of Mars
          for 1281 sols. Dates: 1979-07-19 to 1980-08-07.
  - Completion_Mission - Viking Lander 1 continued to operated in its automatic mode during the
          Completion Mission. The observation sequences were cyclic. VL1 returned
          via direct downlink image and meteorology data about once a week with
          image sequences repeating every 37 sols. The VL1 high-gain antenna was
          programmed to track the Earth until December, 1994. However,
          communications were lost in November 1982 after a command sequence
          uplink. Dates: 1980-08-07 to 1982-11-19.
- Minimum occurrences: 0
- Maximum occurrences: *
- Nillable: No

*missing_scans*
Sometimes vertical scans of data were lost in transmission to Earth or there were errors in the telemetry such 
that scans could not be extracted from the downlink. Missing_scans is the number of vertical lines that are 
missing from an image. A value of zero means no scans were lost.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0

*native_time*
Native time is the local lander time given as a sol number followed by hours, minutes, and seconds past local midnight on that sol. 
Sol 0 is day of landing. The Viking project used the format of sol number, hour, minute, and second for local lander time with times in 
a sol extending beyond 24 hours. This usage is different from the usage by recent Mars rover missions and PDS standard for local time.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*observation_name*
A short note that describes the observation.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*offset_number*
One of 32 offset settings used in the conversion of photodiode voltage to DN.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 31

*product_type_name*
The product_type_name identifies a group of data products within a collection that have some property in common, such as processing 
level, resolution, or instrument-specific setting.
- PDS4 data type: ASCII_Short_String_Collapsed
- Valid values:
  - event_mode - The seismometer acquired data in event mode.
  - high_rate - The seismometer acquired data in high rate mode.
  - detector_temperature - Temperature of Labeled Release beta detector given in degrees celsius.
  - head-end_temperature - Temperature of Labeled Release head-end assembly sensor given in degrees celsius.
  - radioactivity_counts - Radioactivity counts of a Labeled Release cycle.
  - high_resolution_singlet - Single image sequence acquired with the high resolution pixel spacing (0.04 deg.)
  - low_resolution_singlet - Single image sequence acquired with the low resolution pixel spacing (0.12 deg.)
  - color_triplet - Image is part of a three image sequence acquired with one of the color diodes.
  - infrared_triplet - Image is part of a three image sequence acquired with one of the infrared diodes.
  - calibration_level_3 - Calibration data acquired with an internal light source at level 3 (highest).
  - calibration_level_2 - Calibration data acquired with an internal light source at level 2.
  - calibration_level_1 - Calibration data acquired with an internal light source at level 1.
  - calibration_level_0 - Calibration data acquired with an internal light source at level 0 (lowest).
  - scan_verification - Calibration data acquired to test the scanning of the VL camera.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*psa_temperature*
The temperature of the photosensor array (PSA) measured during the acquisition of an VL image.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Unit of measure type: Units_of_Temperature
- Unit id: degC

*rescan_start_sample*
The VL camera could collect data without advancing the azimuth. This was called rescan, i.e., repeating the 
same vertical scan of data. This sometimes happened at the end of image and sometimes was commanded to repeat 
vertical scans. Start_rescan_sample is the sample value where rescan starts in an image. This value is zero
if there was no rescan.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 10000

*rescan_total_samples*
The VL camera could collect data without advancing the azimuth. This was called rescan, i.e., repeating the 
same vertical scan of data. This sometimes happened at the end of image and sometimes was commanded to repeat 
vertical scans. Total_rescan_samples is the total number of rescan scans in an image. This value is zero
if there was no rescan.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0

*sampling_interval*
The spacing in degrees between pixels within a scan line and between scan lines.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0.00
- Maximum value: 0.12
- Unit of measure type: Units_of_Angle
- Unit id: degree

*scan_rate*
The VL camera system has two rates of data collection - 16,000 or 250 bps.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 250
- Maximum value: 16000

*scan_start_azimuth*
Beginning azimuth of an image scan. Values are in the camera-aligned camera coordinate system (CACCS). This 
zero azimuth for each camera generally points towards the other camera.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0.0
- Maximum value: 360.0
- Unit of measure type: Units_of_Angle
- Unit id: degree

*scan_stop_azimuth*
Ending azimuth of an image scan. Values are in the camera-aligned camera coordinate system (CACCS). This zero 
azimuth for each camera generally points towards the other camera.
- PDS4 data type: ASCII_Real
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0.0
- Maximum value: 360.0
- Unit of measure type: Units_of_Angle
- Unit id: degree

*sol_number*
Sol_number is the number of the Mars day on which an observation was acquired. Landing day is Sol 0.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2238
- Comment: See comment for start_sol_number.

*start_sol_number*
Start_sol_number is the number of the Mars day on which a multiple-day observation was begun. Landing day is 
Sol 0.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2238
- Comment: Start/stop_sol_number are provided as an alternative to sol_number for observations that cross one 
or more sol boundaries.

*stop_sol_number*
Stop_sol_number is the number of the Mars day on which a multiple-day observation was ended. Landing day is 
Sol 0.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0
- Maximum value: 2238
- Comment: Start/stop_sol_number are provided as an alternative to sol_number for observations that cross one 
or more sol boundaries.

# Examples

Example PDS4 label snippet for Viking Lander Image product:

```
    <Mission_Area>
      <vikinglander:Viking_Lander_Parameters>
        <vikinglander:Observation_Information>
          <vikinglander:product_type_name>color_triplet</vikinglander:product_type_name>
          <vikinglander:mission_phase_name>Primary_Mission</vikinglander:mission_phase_name>
          <vikinglander:sol_number>3</vikinglander:sol_number>
          <vikinglander:local_hour>15.44</vikinglander:local_hour>
          <vikinglander:observation_name>reference test chart 3</vikinglander:observation_name>
        </vikinglander:Observation_Information>
        <vikinglander:Image_Parameters>
          <vikinglander:diode_name>blue</vikinglander:diode_name>
          <vikinglander:scan_start_azimuth unit="deg">35.0</vikinglander:scan_start_azimuth>
          <vikinglander:scan_stop_azimuth unit="deg">40.0</vikinglander:scan_stop_azimuth>
          <vikinglander:mirror_center_elevation unit="deg">-10.0</vikinglander:mirror_center_elevation>
          <vikinglander:sampling_interval unit="deg">0.12</vikinglander:sampling_interval>
          <vikinglander:offset_number>1</vikinglander:offset_number>
          <vikinglander:gain_number>4</vikinglander:gain_number>
          <vikinglander:psa_temperature unit="degC">15.3</vikinglander:psa_temperature>
          <vikinglander:scan_rate>16000</vikinglander:scan_rate>
          <vikinglander:rescan_start_sample>44</vikinglander:rescan_start_sample>
          <vikinglander:rescan_total_samples>2</vikinglander:rescan_total_samples>
          <vikinglander:missing_scans>0</vikinglander:missing_scans>
          <vikinglander:downlink_path>recorded_uhf_link</vikinglander:downlink_path>
          <vikinglander:dust_flag>false</vikinglander:dust_flag>
        </vikinglander:Image_Parameters>
      </vikinglander:Viking_Lander_Parameters>
    </Mission_Area>
```