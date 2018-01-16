# to-calculate-future-date-and-day-without-using-date-time-module 
months = ['0','January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September',
'October', 'November', 'December']
endings =['0']+ ['st', 'nd', 'rd'] + 17 * ['th'] + ['st', 'nd', 'rd'] + 7 * ['th'] + ['st']
monthdays=['0','31','28','31','30','31','30','31','30','31','30','31','30']
dow=['0','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday']
#case: should not use funtions or oops conepts
year = int(input('Year: '))
month = input('Month (1-12): ')
day = input('Day (1-31): ')
week_day=input('week day: ')
month_number = int(month)
day_number = int(day)
month_name = months[month_number]
ordinal = day + endings[day_number]
print (month_name + ' ' + ordinal + ', ' +str( year))
future_day=int(input('enter no future days: '))
days_in_curntmonth=int(monthdays[month_number])-day_number

if days_in_curntmonth >= future_day :
    ordinal = str((day_number+future_day)) + endings[(day_number+future_day)]
    w=dow.index(week_day)
    ow=future_day%7;l=ow+w
    if ow!=0:
        frd=(l-7 if l>7 else l)
    print(month_name + ' ' + ordinal + ': ',dow[frd] ,str(year))

else:
    nm = future_day - days_in_curntmonth
    month_number+=1
    if month_number==13:month_number=1; year+=1

    while 1:
        if nm>int(monthdays[month_number]):
            nm=nm-int(monthdays[month_number])
            month_number=month_number+1
        if month_number == 13: month_number = 1; year += 1

        else:
            break
    w=dow.index(week_day)
    ow=future_day%7;l=ow+w

    if ow!=0:
        frd=(l-7 if l>7 else l)
    ordinal = str(nm) + endings[nm]

    print(ordinal,':',dow[frd],months[month_number], year)
