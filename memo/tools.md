	
Feature mart class

Load the configuration file (yaml) and able to pass some parameters when creating instances
Extract data from AWS S3
Merge the tables on primary key and set the default values for those cannot be joined
Export the data as parquet files with partitions on specified columns to s3
Create the external table



# Instantiate FeatureMartLoader
loader = FeatureMartLoader(presto_connector, spark, metadata_filename, timekey, parameters)

# Load metadata and set parameters
loader.load_metadata()

# Extract data for the base table
loader.extract_base_table()

# Add features to the base table
loader.add_features()

# Export the transformed data to Parquet files
loader.export_to_parquet()

# Create an external Hive table in Presto
loader.create_external_table()

# Execute the complete process
loader.run()


