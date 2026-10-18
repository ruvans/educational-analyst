let
    Source = Excel.CurrentWorkbook(){[Name="Table1"]}[Content],
    #"Changed Type" = Table.TransformColumnTypes(Source,{{"world_rank", Int64.Type}, {"university_name", type text}, {"country", type text}, {"teaching", type number}, {"international", type number}, {"research", type number}, {"citations", type number}, {"income", type any}, {"total_score", type number}, {"num_students", Int64.Type}, {"student_staff_ratio", type number}, {"international_students", type number}, {"female_male_ratio", type any}, {"year", Int64.Type}}),
    #"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"world_rank", "teaching", "research", "citations", "income", "student_staff_ratio", "female_male_ratio", "international"}),
    #"Removed Errors" = Table.RemoveRowsWithErrors(#"Removed Columns", {"total_score"}),
    #"Filtered empty num_students" = Table.SelectRows(#"Removed Errors", each [num_students] <> null and [num_students] <> ""),
    #"Filtered empty international_students" = Table.SelectRows(#"Filtered empty num_students", each [international_students] <> null and [international_students] <> ""),
    #"Renamed Columns" = Table.RenameColumns(#"Filtered empty international_students",{{"international_students", "international_students_percentage"}}),
    #"Changed new column type" = Table.TransformColumnTypes(#"Renamed Columns",{{"international_students_percentage", Percentage.Type}}),
    #"Added Custom" = Table.AddColumn(#"Changed new column type", "num_international_students", each [num_students]*[international_students_percentage]),
    #"Rounded Off" = Table.TransformColumns(#"Added Custom",{{"num_international_students", each Number.Round(_, 0), type number}})
in
    #"Rounded Off"
