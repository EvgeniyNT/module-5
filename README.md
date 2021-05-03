ТАБЛИЦА ods_payment

#Общая проверка таблицы
Проверка корректности структуры таблицы. Проверяем наличие колонок в соответствии со списком:
batch.expect_table_columns_to_match_set(column_set=["user_id", "billing_period", "service", "tariff", "sum", "created_at"], exact_match=False)
Проверка целостности таблицы. Проверяем минимальлное количество записей:
batch.expect_table_row_count_to_be_between(min_value=1000)

#Проверка колонки user_id
Проверяем качество данных на предмет соответствия типа данных в колонке. Данные в колонке должны быть цифровыми:
batch.expect_column_values_to_be_of_type (column='user_id', type_='INTEGER')

#Проверка колонки pay_doc_type
Проверяем качество данных на предмет наличия конкретных видов требуемых значений. Проводим проверку содержания колонки на соответствие значений списку:
batch.expect_column_distinct_values_to_be_in_set(column="pay_doc_type", value_set=["MASTER", "MIR", "VISA"])

#Проверка колонки pay_doc_num
Проверяем целостность данных - проверяем содержание колонки на отсутствие NULL:
batch.expect_column_values_to_not_be_null(column='pay_doc_num')

#Проверка колонки account
Проверяем длину поля в колонке. Поле должно быть не менее 4х знаков:
batch.expect_column_value_lengths_to_be_between(column="account", min_value=4)

#Проверка колонки pay_date
Проверяем диапазоны дат на соответствие требуемому интервалу:
batch.expect_column_values_to_be_between(column="pay_date", max_value="2022-01-01 00:00:00", min_value="2012-01-02 00:00:00", parse_strings_as_datetimes=True)

#Проверка колонки phone
Проверяем поле на соответствие формату записи телефона +xxxxxxxxxxx:
batch.expect_column_values_to_match_regex(column="phone",regex="\+\d{11}")

#Проверка колонки sum
Проверяем на отсутствие отрицательных значений колонки
batch.expect_column_min_to_be_between(column="sum", min_value=0.0, strict_min=True)

#Проверка колонки billing_period
Проверяем колонку на соответствие типу:
batch.expect_column_values_to_be_in_type_list(column="billing_period",type_list=["TEXT",],))

------------------------------------------------------------------------------------------------

ТАБЛИЦА ods_issue

#Общая проверка таблицы
Проверка корректности структуры таблицы. Проверяем наличие колонок в соответствии со списком:
batch.expect_table_columns_to_match_set(column_set=["user_id", "start_time", "end_time", "title", "description", "service"], exact_match=False)
Проверка целостности таблицы. Проверяем минимальлное количество записей:
batch.expect_table_row_count_to_be_between(min_value=1000)

#Проверка колонки user_id
Проверяем качество данных на предмет соответствия типа данных в колонке. Данные в колонке должны быть цифровыми:
batch.expect_column_values_to_be_of_type (column='user_id', type_='INTEGER')

#Проверка колонки title
Проверка целостности данных, проверяем колонку на соответствие типу:
batch.expect_column_values_to_be_in_type_list(column="title", type_list=["TEXT",],)

#Проверка колонки description
Проверяем целостность данных - проверяем содержание колонки на отсутствие NULL:
batch.expect_column_values_to_not_be_null(column="description")

#Проверка колонки service
Проверяем качество данных на предмет наличия конкретных видов требуемых значений. Проводим проверку содержания колонки на соответствие значений списку:
batch.expect_column_values_to_be_in_set(column="service", value_set=["Connect", "Disconnect", "Setup Environment"])

#Проверка колонки start_time
Проверяем целостность данных. Дата не должна быть ранее чем 2012-01-01:
batch.expect_column_min_to_be_between(column="start_time", min_value='2012-01-01', strict_min=True, parse_strings_as_datetimes=False)

#Проверка колонки end_time
Проверяем целостность данных. Дата не должна быть позднее чем 2022-01-01:
batch.expect_column_max_to_be_between(column="end_time", max_value='2022-01-01', strict_max=True, parse_strings_as_datetimes=False)

-------------------------------------------------------------------------------------------------------

ТАБЛИЦА ods_billing

#Общая проверка таблицы
Проверка корректности структуры таблицы. Проверяем наличие колонок в соответствии со списком:
batch.expect_table_columns_to_match_set(column_set=["user_id", "billing_period", "service", "tariff", "sum", "created_at"], exact_match=False)
Проверка целостности таблицы. Проверяем минимальлное количество записей:
batch.expect_table_row_count_to_be_between(min_value=1000)

#Проверка колонки user_id
Проверяем качество данных на предмет соответствия типа данных в колонке. Данные в колонке должны быть цифровыми:
batch.expect_column_values_to_be_of_type (column='user_id', type_='INTEGER')

#Проверка колонки service
Проверяем целостность данных - проверяем содержание колонки на отсутствие NULL:
batch.expect_column_values_to_not_be_null(column="service")

#Проверка колонки tariff
Проверяем качество данных на предмет наличия конкретных видов требуемых значений. Проводим проверку содержания колонки на соответствие значений списку:
batch.expect_column_values_to_be_in_set(column="tariff", value_set=["Gigabyte", "Maxi", "Megabyte", "Mini"])

#Проверка колонки sum
Проверяем качество данных на предмет возможных максимальных значений - значение поля не может быть более 999999
batch.expect_column_max_to_be_between(column="sum", max_value=999999.9, strict_max=True)

#Проверка колонки billing_period
Проверяем целостность данных. Дата не должна быть ранее чем 2012-01-01:
batch.expect_column_min_to_be_between(column="billing_period", min_value='2012-01-01', strict_min=True, parse_strings_as_datetimes=False)

#Проверка колонки created_at
Проверяем целостность данных. Дата не должна быть позднее чем 2022-01-01:
batch.expect_column_max_to_be_between(column="created_at", max_value='2022-01-01', strict_max=True, parse_strings_as_datetimes=False)

-----------------------------------------------------------------------------------------------------------

ТАБЛИЦА ods_traffic
Проверка корректности структуры таблицы. Проверяем наличие колонок в соответствии со списком:
batch.expect_table_columns_to_match_set(column_set=["user_id", "timestamp", "device_id", "device_ip_addr", "bytes_sent", "bytes_received"], exact_match=False)
Проверка целостности таблицы. Проверяем минимальлное количество записей:
batch.expect_table_row_count_to_be_between(min_value=1000)

#Проверка колонки user_id
Проверяем качество данных на предмет соответствия типа данных в колонке. Данные в колонке должны быть цифровыми:
batch.expect_column_values_to_be_of_type (column='user_id', type_='INTEGER')

#Проверка колонки timestamp
Проверяем целостность данных - проверяем содержание колонки на отсутствие NULL:
batch.expect_column_values_to_not_be_null(column="timestamp")

#Проверка колонки device_serial
Проверяем длину поля в колонке. Поле должно быть не менее 4х знаков:
batch.expect_column_value_lengths_to_be_between(column="device_id", min_value=4)

#Проверка колонки device_ip_addr
Проверяем целостность данных - проверяем содержание колонки на отсутствие NULL:
batch.expect_column_values_to_not_be_null(column="device_ip_addr")

#Проверка колонки bytes_sent
Проверяем целостность данных - значение поля должно быть больше 0:
batch.expect_column_min_to_be_between(column="bytes_sent", min_value=0, strict_min=True)

#Проверка колонки bytes_received
Проверяем целостность данных - значение поля должно быть больше 0:
batch.expect_column_min_to_be_between(column="bytes_received", min_value=0, strict_min=True)

-----------------------------------------------------------------------------------------------------------------
