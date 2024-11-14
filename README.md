library(RODBC)
dsn_driver <- "{IBM DB2 ODBC Driver}"
dsn_database <- "bludb"
dsn_hostname <- "*****"
dsn_port <- "31505"
dsn_protocol <- "TCPIP"
dsn_uid <- "******"
dsn_pwd <- "******"
dsn_security <- "ssl"

conn_path <- paste("DRIVER=", dsn_driver,
                   ";DATABASE=", dsn_database,
                   ";HOSTNAME=", dsn_hostname,
                   ";PORT=", dsn_port,
                   ";PROTOCOL=", dsn_protocol,
                   ";UID=", dsn_uid,
                   ";PWD=", dsn_pwd,
                   ";SECURITY=", dsn_security,
                   sep="")
conn <- odbcDriverConnect(conn_path)

# Dump connection info
sql.info <- sqlTypeInfo(conn)
conn.info <- odbcGetInfo(conn)
conn.info["DBMS_Name"]
conn.info["DBMS_Ver"]
conn.info["Driver_ODBC_Ver"]

attributes(conn)

#Task 1 - Record Count
#Determine how many records are in the seoul_bike_sharing dataset.
# provide your solution here
query = "SELECT count(*) AS record_count FROM seoul_bike_sharing dataset"
sqlQuery(conn,query)
