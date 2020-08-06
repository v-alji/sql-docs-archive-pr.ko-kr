---
title: 달력 인식 날짜 및 시간 UDT 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: cfcf8516-0e7b-4ca4-8bd8-8b2511a50308
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 115b35c394397f7b7ec3242571d5e91d55305451
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648541"
---
# <a name="calendar-aware-date-and-time-udt-sample"></a><span data-ttu-id="ef677-102">달력 인식 날짜 및 시간 UDT 샘플</span><span class="sxs-lookup"><span data-stu-id="ef677-102">Calendar-Aware Date and Time UDT Sample</span></span>
  <span data-ttu-id="ef677-103">사용되는 달력 시스템에 대한 인식 부족으로 날짜의 의미를 잘 모르는 상태에서 날짜를 문자열로 저장하면 혼동될 수 있습니다. `CADatetime` 예제에서는 달력을 사용하여 날짜와 시간을 처리할 수 있는 두 개의 사용자 정의 데이터 형식(`CADatetime` 및 `CADate`)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-103">Storing dates as strings can be confusing because dates are meaningless without understanding what calendar system is being used.The `CADatetime` sample defines two user-defined data types, `CADatetime` and `CADate`, which provide calendar-aware handling of dates and times.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef677-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ef677-104">Prerequisites</span></span>  
 <span data-ttu-id="ef677-105">이 프로젝트를 만들고 실행하려면 다음 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-105">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ef677-106">또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="ef677-106">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="ef677-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 설명서 및 예제 [웹 사이트](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-107">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="ef677-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개발자 [웹 사이트](https://go.microsoft.com/fwlink/?linkid=62796)에서 제공되는 AdventureWorks 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="ef677-108">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="ef677-109">.NET Framework SDK 2.0 이상 또는 Microsoft Visual Studio 2005 이상.</span><span class="sxs-lookup"><span data-stu-id="ef677-109">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="ef677-110">.NET Framework SDK는 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-110">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="ef677-111">또한 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-111">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="ef677-112">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 CLR 통합이 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="ef677-113">CLR 통합을 설정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-113">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="ef677-114">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="ef677-114">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="ef677-115">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-115">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef677-116">CLR을 사용하도록 설정하려면 `ALTER SETTINGS` 서버 수준 사용 권한이 있어야 합니다. 이 사용 권한은 `sysadmin` 및 `serveradmin` 고정 서버 역할의 멤버가 암시적으로 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-116">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="ef677-117">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 AdventureWorks 데이터베이스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-117">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="ef677-118">사용 중인 인스턴스의 관리자가 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치를 완료 하려면 관리자에 게 **createassembly** 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-118">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="ef677-119">예제 빌드</span><span class="sxs-lookup"><span data-stu-id="ef677-119">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="ef677-120">다음 지침을 사용하여 예제를 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-120">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="ef677-121">Visual Studio 또는 .NET Framework 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-121">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="ef677-122">필요한 경우 예제에 대한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-122">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="ef677-123">이 예에서는 C:\MySample을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-123">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="ef677-124">c:\MySample에서 `CalendarAware.cs`를 만들고 C# 예제 코드(아래)를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-124">In c:\MySample, create `CalendarAware.cs` and copy the C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="ef677-125">c:\MySample에서 `calendars.txt` 파일을 만들고 예제 코드를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-125">In c:\MySample, create the file `calendars.txt` and copy the sample code into the file.</span></span>  
  
5.  <span data-ttu-id="ef677-126">c:\MySample에서 `calendars.ar-SA.txt` 파일을 만들고 다음을 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-126">In c:\MySample, create the file `calendars.ar-SA.txt` and copy the following into the file:</span></span>  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 1`  
  
6.  <span data-ttu-id="ef677-127">c:\MySample에서 `calendars.ja.txt` 파일을 만들고 다음을 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-127">In c:\MySample, create the file `calendars.ja.txt` and copy the following into the file:</span></span>  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 3`  
  
7.  <span data-ttu-id="ef677-128">c:\MySample에서 `calendars.``zh-CN.txt` 파일을 만들고 다음을 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-128">In c:\MySample, create the file `calendars.``zh-CN.txt` and copy the following into the file:</span></span>  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 8`  
  
8.  <span data-ttu-id="ef677-129">c:\MySample에서 `build.com` 파일을 만들고 다음을 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-129">In c:\MySample, create the file `build.com` and copy the following into the file:</span></span>  
  
    -   `resgen calendars.txt`  
  
    -   `resgen calendars.ar-SA.txt`  
  
    -   `resgen calendars.ja.txt`  
  
    -   `resgen calendars.zh-CN.txt`  
  
    -   `al /t:lib /culture:ar-SA /embed:calendars.ar-SA.resources /out:CADatetime.resources.ar-SA.dll`  
  
    -   `al /t:lib /culture:ja /embed:calendars.ja.resources /out:CADatetime.resources.ja.dll`  
  
    -   `al /t:lib /culture:zh-CN /embed:calendars.zh-CN.resources /out:CADatetime.resources.zh-CN.dll`  
  
    -   `al /t:lib /culture:"" /embed:calendars.resources /out:CADatetime.resources.dll`  
  
9. <span data-ttu-id="ef677-130">명령 프롬프트에서 파일 빌드를 실행하여 위성 어셈블리를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-130">Build the satellite assembles by executing the file build at the command prompt.</span></span>  
  
10. <span data-ttu-id="ef677-131">다음을 실행하여 명령줄 프롬프트에서 예제 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-131">Compile the sample code from the command line prompt by executing the following:</span></span>  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:CADateTime.dll /target:library CalendarAwareDate.cs`  
  
11. <span data-ttu-id="ef677-132">[!INCLUDE[tsql](../../includes/tsql-md.md)] 설치 코드를 파일에 복사하고 해당 파일을 예제 디렉터리에 `Install.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-132">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
12. <span data-ttu-id="ef677-133">예제가 `C:\MySample\`이외의 디렉터리에 설치된 경우 해당 위치를 가리키도록 표시된 대로 `Install.sql` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-133">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
13. <span data-ttu-id="ef677-134">다음을 실행하여 어셈블리 및 저장 프로시저를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-134">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
14. <span data-ttu-id="ef677-135">[!INCLUDE[tsql](../../includes/tsql-md.md)] 테스트 명령 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `test.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-135">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
15. <span data-ttu-id="ef677-136">다음 명령으로 테스트 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-136">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
16. <span data-ttu-id="ef677-137">[!INCLUDE[tsql](../../includes/tsql-md.md)] 정리 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `cleanup.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-137">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
17. <span data-ttu-id="ef677-138">다음 명령으로 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-138">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="ef677-139">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="ef677-139">Sample Code</span></span>  
 <span data-ttu-id="ef677-140">다음은 이 예제에 대한 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-140">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="ef677-141">C#</span><span class="sxs-lookup"><span data-stu-id="ef677-141">C#</span></span>  
  
```  
    using System;  
    using System.Data.Sql;  
    using System.Data.SqlTypes;  
    using System.Globalization;  
    using System.Resources;  
    using System.Text;  
    using System.Reflection;  
    using System.Collections.Generic;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using System.Xml.Schema;  
    using System.IO;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
  
    /// <summary>  
    /// A date value in the specified calendar system.  
    /// </summary>  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedType(Microsoft.SqlServer.Server.Format.Native, IsByteOrdered = true)]  
    public struct CADate : INullable, IXmlSerializable  
    {  
        // This type uses days == 0 as the way to designate a NULL value  
  
        const string CADateSchema =  
            "<xs:schema targetNamespace=\"https://schemas.microsoft.com/sqlserver/2004/08/CADate\" " +  
                "xmlns=\"https://schemas.microsoft.com/sqlserver/2004/07/CADate\" " +  
                "elementFormDefault=\"qualified\"" +  
                "xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" >" +  
                "<xs:element name=\"CADate\" >" +  
                    "<xs:complexType mixed=\"true\" >" +  
                        "<xs:attribute name=\"IsNull\" use=\"required\" type=\"xs:boolean\" />" +  
                        "<xs:attribute name=\"Year\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Month\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Day\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Calendar\" type=\"xs:string\"/>" +  
                    "</xs:complexType>" +  
                "</xs:element>" +  
            "</xs:schema>";  
  
        private const uint NullDay = 0;  
  
        private static readonly char[] dateChars = new char[] { 'd', 'M', 'y' };  
        private static readonly char[] allowedSinglePatternChars = new char[] { 'd', 'D', 'm', 'M', 'y', 'Y', '/', '%' };  
        private static readonly char[] allowedDoublePatternChars = new char[] { 'g', '\\' };  
  
        /// <summary>  
        ///     Each tick is 100 nanoseconds.  This conversion factor when multiplied by the number of  
        ///     days yields the number of ticks which make up that day.  Ticks are interesting as they  
        ///     can be used to construct DateTime instances in order to perform various date based computations.  
        /// </summary>  
        private const long DaysToTicksConversionFactor = 10L * 1000L * 1000L * 60L * 60L * 24L;  
  
        /// <summary>  
        /// The number of days since the calendar started (January 1, 1)  
        /// </summary>  
        private uint days;  
  
        /// <summary>  
        /// Which calendar is used for this date and time  
        /// </summary>  
        private byte calendarId;  
  
        /// <summary>  
        /// construct a CADate from the specified datetime using the default calendar.  
        /// </summary>  
        /// <param name="dt">DateTime</param>  
        public CADate(DateTime dt)  
            : this(dt, CalendarInfo.DefaultCalendarId)  
        {  
        }  
  
        /// <summary>  
        /// Construct a calendar aware date for the specified year/month/day using the default calendar  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        public CADate(int year, int month, int day)  
            : this(new DateTime(year, month, day, CalendarInfo.DefaultCalendar))  
        {  
        }  
  
        /// <summary>  
        ///     Converts a DateTime instance and a calendar into a calendar aware date instance.  
        /// </summary>  
        /// <param name="dt">A specific point in time</param>  
        /// <param name="calendarId">A specific calendar system</param>  
        private CADate(DateTime dt, int calendarId)  
        {  
            this.days = (uint)(dt.Ticks / DaysToTicksConversionFactor);  
            this.calendarId = (byte)calendarId;  
        }  
  
        /// <summary>  
        /// the current CADate  
        /// </summary>  
        /// <value></value>  
        public static CADate Now  
        {  
            get  
            {  
                return new CADate(DateTime.Now);  
            }  
        }  
  
        public static string CurrentCalendarName  
        {  
            get  
            {  
                return CalendarInfo.DefaultCalendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// return the null value for this type  
        /// </summary>  
        /// <value></value>  
        public static CADate Null  
        {  
            get  
            {  
                CADate caDate = new CADate();  
                caDate.days = NullDay;  
  
                return caDate;  
            }  
        }  
  
        /// <summary>  
        /// is this value null  
        /// </summary>  
        /// <value></value>  
        public bool IsNull  
        {  
            get  
            {  
                return this.days == NullDay;  
            }  
        }  
  
        public Calendar Calendar  
        {  
            get  
            {  
                return CalendarInfo.Calendars[this.calendarId];  
            }  
        }  
  
        public string CalendarName  
        {  
            get  
            {  
                return this.Calendar.GetType().Name;  
            }  
        }  
  
        // Accessors for parts of the date   
  
        public int Year  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetYear(this.DateTime);  
            }  
        }  
  
        public int Month  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMonth(this.DateTime);  
            }  
        }  
  
        public int DayOfMonth  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfMonth(this.DateTime);  
            }  
        }  
  
        public int Day  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfYear(this.DateTime);  
            }  
        }  
  
        public uint Days  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.days;  
            }  
        }  
  
        /// <summary>  
        /// convert to datetime  
        /// </summary>  
        /// <value></value>  
        public DateTime DateTime  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return new DateTime(this.Days * DaysToTicksConversionFactor);  
            }  
        }  
  
        /// <summary>  
        /// parse the given string and return a calendar aware date.  
        /// </summary>  
        /// <param name="sqlString"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate Parse(SqlString sqlString)  
        {  
            if (sqlString.IsNull)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(DateTime.Parse(sqlString.Value, DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Construct a CADate from the specified format, using the current culture  
        /// </summary>  
        /// <param name="data">the string to be parsed</param>  
        /// <param name="format">the format string</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate ParseUsingFormat(string data, string format)  
        {  
            if (data == null || format == null)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(  
                DateTime.ParseExact(  
                data,  
                FilterDateFormat(format),  
                DateTimeFormatInfo.CurrentInfo));  
        }  
  
        // The following methods are intended to be callable from tsql.  That is why they are static.  
  
        /// <summary>  
        /// Create a new CADate from a SqlDateTime  
        /// </summary>  
        /// <param name="sqlDateTime"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromSqlDateTime(SqlDateTime sqlDateTime)  
        {  
            if (sqlDateTime.IsNull)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(sqlDateTime.Value);  
        }  
  
        /// <summary>  
        /// Creates a CADateTime from a Sql DateTime instance and a specific calendar.  
        /// </summary>  
        /// <param name="sqlDateTime">When</param>  
        /// <param name="calendarName">The short name of the desired calendar</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = true, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromSqlDateTimeAndCalendar(SqlDateTime sqlDateTime, string calendarName)  
        {  
            return new CADate(sqlDateTime.Value, CalendarInfo.GetCalendarId(calendarName));  
        }  
  
        /// <summary>  
        /// Create a new CADate from the year/month/day  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromYearMonthDay(int year, int month, int day)  
        {  
            return new CADate(year, month, day);  
        }  
  
        public static SqlBoolean operator ==(CADate xCADate, CADate yCADate)  
        {  
            if (xCADate.IsNull || yCADate.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADate.DateTime == yCADate.DateTime;  
        }  
  
        public static SqlBoolean operator !=(CADate xCADate, CADate yCADate)  
        {  
            if (xCADate.IsNull || yCADate.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADate.DateTime != yCADate.DateTime;  
        }  
  
        // Conversions to other representations of the date  
  
        /// <summary>  
        /// convert the date to string  
        /// </summary>  
        /// <returns></returns>  
        public override string ToString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return string.Format(  
                CultureInfo.CurrentUICulture,  
                DayMonthYearFormatString(),  
                this.DayOfMonth,  
                this.Month,  
                this.Year);  
        }  
  
        /// <summary>  
        /// Return a string representation of this date, in the Gregorian calendarId  
        /// </summary>  
        /// <returns></returns>  
        public string ToGregorianString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString("d", DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Convert the date to string, using the specified format  
        /// </summary>  
        /// <param name="format">Format string</param>  
        /// <returns></returns>  
        public string ToGregorianStringUsingFormat(string format)  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(  
                FilterDateFormat(format),  
                DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Convert to sql datetime  
        /// </summary>  
        /// <returns></returns>  
        public SqlDateTime ToSqlDateTime()  
        {  
            return new SqlDateTime(this.DateTime);  
        }  
  
        // Manipulation of date parts  
  
        public CADate AddYears(int years)  
        {  
            return new CADate(this.Calendar.AddYears(this.DateTime, years));  
        }  
  
        public CADate AddDays(int daysToAdd)  
        {  
            return new CADate(this.Calendar.AddDays(this.DateTime, daysToAdd));  
        }  
  
        public CADate AddMonths(int months)  
        {  
            return new CADate(this.Calendar.AddMonths(this.DateTime, months));  
        }  
  
        public double DiffDays(CADate other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalDays;  
        }  
  
        // Hashing and comparison methods  
  
        public override int GetHashCode()  
        {  
            return this.DateTime.GetHashCode();  
        }  
  
        public override bool Equals(object obj)  
        {  
            if (!(obj is DateTime))  
            {  
                return false;  
            }  
  
            DateTime dt = (DateTime)obj;  
            return this.DateTime.Equals(dt);  
        }  
  
        public XmlSchema GetSchema()  
        {  
            StringReader sr = new StringReader(CADateSchema);  
            XmlSchema schema = XmlSchema.Read(  
                sr,  
                new ValidationEventHandler(this.ValidationHandler));  
            sr.Dispose();  
  
            return schema;  
        }  
  
        public void ReadXml(XmlReader reader)  
        {  
            if (reader == null)  
            {  
                throw new ArgumentNullException("reader");  
            }  
  
            reader.MoveToContent();  
            if (reader.GetAttribute("IsNull").Equals("true"))  
            {  
                this.days = NullDay;  
            }  
            else  
            {  
                string calendarName = reader.GetAttribute("Calendar");  
                Calendar requestedCalendar   
                    = CalendarInfo.Calendars[CalendarInfo.GetCalendarId(calendarName)];  
  
                this.days = (uint)(new DateTime(  
                    int.Parse(  
                        reader.GetAttribute("Year"),  
                        CultureInfo.CurrentUICulture),  
                    int.Parse(  
                        reader.GetAttribute("Month"),   
                        CultureInfo.CurrentUICulture),  
                    int.Parse(  
                        reader.GetAttribute("Day"),   
                        CultureInfo.CurrentUICulture),  
                        requestedCalendar).Ticks / DaysToTicksConversionFactor);  
            }  
        }  
  
        public void WriteXml(XmlWriter writer)  
        {  
            if (writer == null)  
            {  
                throw new ArgumentNullException("writer");  
            }  
  
            writer.WriteStartElement(  
                "CADate",  
                "https://schemas.microsoft.com/sqlserver/2004/08/CADate");  
            writer.WriteAttributeString("IsNull", this.IsNull.ToString(CultureInfo.CurrentUICulture));  
            if (!this.IsNull)  
            {  
                writer.WriteAttributeString("Year", this.Year.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Month", this.Month.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Day", this.Day.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Calendar", this.Calendar.GetType().ToString());  
            }  
  
            writer.WriteEndElement();  
        }  
  
        // DateTime.ParseExact takes a "format" string which describes how to present the date and time.  
        // This method filters out any formatting characters which conflict   
        private static string FilterDateFormat(string format)  
        {  
            StringBuilder sb = new StringBuilder(format.Length);  
            for (int i = 0; i < format.Length; i++)  
            {  
                char element = format[i];  
                bool doubled = (i + 1 < format.Length)  
                    && (element.Equals(format[i + 1]) || element.Equals('\\'));  
                if (Array.IndexOf<char>(allowedSinglePatternChars, element) > -1 ||  
                    char.IsWhiteSpace(element))  
                {  
                    sb.Append(element);  
                }  
                else if (doubled && (Array.IndexOf<char>(allowedDoublePatternChars, element) > -1))  
                {  
                    sb.Append(element);  
                    sb.Append(format[++i]);  
                }  
            }  
  
            return sb.ToString();  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // day, month, and year components in a culture appropriate way.  
        private static string DayMonthYearFormatString()  
        {  
            string cultureDatePattern = CultureInfo.CurrentCulture.DateTimeFormat.ShortDatePattern;  
            return CalendarInfo.SubstitutePositionForCharacters(dateChars, cultureDatePattern);  
        }  
  
        private void ValidationHandler(object sender, ValidationEventArgs args)  
        {  
            throw new ApplicationException(args.Message);  
        }  
    }  
    public static class CalendarInfo  
    {  
        public const byte MaxCalendarId = 0xff;  
        private readonly static char[] stringFormatChars; // = new char[] { 't' };  
        private static readonly Calendar defaultCalendar; // = new GregorianCalendar();  
        private static readonly int defaultCalendarId;  
        private static readonly Calendar[] calendars;  
  
        /// <summary>  
        /// Initialize the calendar array, one for each possible calendar  
        /// </summary>  
        static CalendarInfo()  
        {  
            stringFormatChars = new char[] { 't' };  
  
            ResourceManager rm = new ResourceManager("calendars", Assembly.GetExecutingAssembly());  
  
            int numCalendars = int.Parse(rm.GetString("NumCalendars"), CultureInfo.CurrentUICulture);  
            if (numCalendars > MaxCalendarId)  
            {  
                throw new ArgumentOutOfRangeException("Does not support more than 255 calendars");  
            }  
  
            calendars = new Calendar[numCalendars];  
            for (int i = 0; i < numCalendars; i++)  
            {  
                string typeName = rm.GetString(i.ToString(CultureInfo.CurrentUICulture));  
                calendars[i] = (Calendar)Activator.CreateInstance(Type.GetType(typeName, true));  
            }  
  
            defaultCalendarId = int.Parse(rm.GetString("DefaultCalendarID"), CultureInfo.CurrentUICulture);  
            defaultCalendar = calendars[defaultCalendarId];  
        }  
  
        public static Calendar DefaultCalendar  
        {  
            get  
            {  
                return CalendarInfo.defaultCalendar;  
            }  
        }  
  
        public static int DefaultCalendarId  
        {  
            get  
            {  
                return CalendarInfo.defaultCalendarId;  
            }  
        }  
  
        public static Calendar[] Calendars  
        {  
            get  
            {  
                return CalendarInfo.calendars;  
            }  
        }  
  
        public static int GetCalendarId(string calendarName)  
        {  
            for (int i = 0; i < calendars.Length; i++)  
            {  
                if (calendars[i].GetType().Name == calendarName)  
                {  
                    return i;  
                }  
            }  
  
            throw new ArgumentException("Unknown calendar: " + calendarName);  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // either date or datetime components in a culture appropriate way.  
        public static string SubstitutePositionForCharacters(Char[] characters, string pattern)  
        {  
            StringBuilder sb = new StringBuilder();  
            char lastChar = ' ';  
            for (int i = 0; i < pattern.Length; i++)  
            {  
                char c = pattern[i];  
                int position = Array.IndexOf<char>(characters, c);  
                if (position != -1)  
                {  
                    if (lastChar != c)  
                    {  
                        sb.Append('{');  
                        sb.Append(position);  
  
                        // If this isn't a string format char, it is a numeric format char.  
                        // In that case we need to get the correct number of digits from  
                        // the pattern.  
                        if (Array.IndexOf<char>(stringFormatChars, c) == -1)  
                        {  
                            // Decimal number with the appropriate minimum number of digits  
                            sb.AppendFormat(":d{0:d}", CountRun(c, pattern, i));  
                        }  
  
                        sb.Append('}');  
                    }  
                }  
                else  
                {  
                    sb.Append(c);  
                }  
  
                lastChar = c;  
            }  
  
            return sb.ToString();  
        }  
  
        // Given that you have found character c in a pattern, count how many instances of that  
        // character occur at that position before another character or the end of the string is reached.  
  
        public static int CountRun(char chr, string pattern, int start)  
        {  
            if (pattern == null)  
            {  
                throw new ArgumentNullException("pattern");  
            }  
  
            int result = 1;  
            for (int i = start + 1; i < pattern.Length; i++)  
            {  
                if (pattern[i] == chr)  
                {  
                    result += 1;  
                }  
                else  
                {  
                    break;  
                }  
            }  
  
            return result;  
        }  
    }  
    /// <summary>  
    /// A datetime value in the specified calendar system.  
    /// </summary>  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedType(Microsoft.SqlServer.Server.Format.Native, IsByteOrdered = true, ValidationMethodName = "IsValid")]  
    public struct CADateTime : INullable, IXmlSerializable  
    {  
        const string CADateTimeSchema =  
            "<xs:schema targetNamespace=\"https://schemas.microsoft.com/sqlserver/2004/08/CADateTime\" " +  
                "xmlns=\"https://schemas.microsoft.com/sqlserver/2004/07/CADate\" " +  
                "elementFormDefault=\"qualified\"" +  
                "xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" >" +  
                "<xs:element name=\"CADate\" >" +  
                    "<xs:complexType mixed=\"true\" >" +  
                        "<xs:attribute name=\"IsNull\" use=\"required\" type=\"xs:boolean\" />" +  
                        "<xs:attribute name=\"Year\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Month\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Day\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Hour\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Minute\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Second\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Calendar\" type=\"xs:string\"/>" +  
                    "</xs:complexType>" +  
                "</xs:element>" +  
            "</xs:schema>";  
  
        static readonly char[] datetimeChars = new char[] { 'd', 'M', 'y', 'h', 'H', 'm', 's', 't' };  
  
        // This type uses ticks == 0 as the way to designate a NULL value  
        private const long NullTicks = 0;  
  
        /// <summary>  
        /// What date and time this is as ticks from midnight January 1, 1  
        /// </summary>  
        private long dtTicks;  
  
        /// <summary>  
        /// Which calendar is used for this date and time  
        /// </summary>  
        private byte calendarId;  
  
        /// <summary>  
        /// Construct a CADateTime from the specified datetime using the default calendar.  
        /// </summary>  
        /// <param name="dt">DateTime</param>  
        public CADateTime(DateTime dt)  
            : this(dt, CalendarInfo.DefaultCalendarId)  
        {  
        }  
  
        /// <summary>  
        /// Construct a calendar aware datetime for the specified year/month/day using the default calendar  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        public CADateTime(int year, int month, int day)  
            : this(new DateTime(year, month, day, CalendarInfo.DefaultCalendar))  
        {  
        }  
  
        /// <summary>  
        ///     Converts a DateTime instance and a calendar into a calendar aware datetime instance.  
        /// </summary>  
        /// <param name="dt">A specific point in time</param>  
        /// <param name="calendarId">A specific calendar system</param>  
        private CADateTime(DateTime dt, int calendarId)  
        {  
            this.dtTicks = dt.Ticks;  
            this.calendarId = (byte)calendarId;  
        }  
  
        /// <summary>  
        /// return the null value for this type  
        /// </summary>  
        /// <value></value>  
        public static CADateTime Null  
        {  
            get  
            {  
                CADateTime dt = new CADateTime();  
                dt.dtTicks = NullTicks;  
  
                return dt;  
            }  
        }  
  
        /// <summary>  
        /// the current CADateTime  
        /// </summary>  
        /// <value></value>  
        public static CADateTime Now  
        {  
            get  
            {  
                return new CADateTime(DateTime.Now);  
            }  
        }  
  
        public static string CurrentCalendarName  
        {  
            get  
            {  
                return CalendarInfo.DefaultCalendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// is this value null  
        /// </summary>  
        /// <value></value>  
        public bool IsNull  
        {  
            get  
            {  
                return this.Ticks == NullTicks;  
            }  
        }  
  
        public int Year  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetYear(this.DateTime);  
            }  
        }  
  
        public int Month  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMonth(this.DateTime);  
            }  
        }  
  
        public int DayOfMonth  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfMonth(this.DateTime);  
            }  
        }  
  
        public int Day  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfYear(this.DateTime);  
            }  
        }  
  
        public int Hour  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetHour(this.DateTime);  
            }  
        }  
  
        public int Minute  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMinute(this.DateTime);  
            }  
        }  
  
        public int Second  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetSecond(this.DateTime);  
            }  
        }  
  
        /// <summary>  
        /// Milliseconds  
        /// </summary>  
        /// <value></value>  
        public double Milliseconds  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMilliseconds(this.DateTime);  
            }  
        }  
  
        public long Ticks  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.dtTicks;  
            }  
        }  
  
        /// <summary>  
        /// convert to datetime  
        /// </summary>  
        /// <value></value>  
        public DateTime DateTime  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get { return new DateTime(this.dtTicks); }  
        }  
  
        public Calendar Calendar  
        {  
            get  
            {  
                return CalendarInfo.Calendars[this.calendarId];  
            }  
        }  
  
        public string CalendarName  
        {  
            get  
            {  
                return this.Calendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// parse the given string and return a calendar aware datetime.  
        /// </summary>  
        /// <param name="sqlString"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime Parse(SqlString sqlString)  
        {  
            if (sqlString.IsNull)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(  
                DateTime.Parse(  
                    sqlString.Value,  
                    DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Construct a CADateTime from the specified format, using the current culture  
        /// </summary>  
        /// <param name="data">the string to be parsed</param>  
        /// <param name="format">the format string</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime ParseUsingFormat(string data, string format)  
        {  
            if (data == null || format == null)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(DateTime.ParseExact(data, format, DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Create a new CADateTime from a SqlDateTime  
        /// </summary>  
        /// <param name="sqlDateTime"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromSqlDateTime(SqlDateTime sqlDateTime)  
        {  
            if (sqlDateTime.IsNull)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(sqlDateTime.Value);  
        }  
  
        /// <summary>  
        /// Creates a CADateTime from a Sql DateTime instance and a specific calendar.  
        /// </summary>  
        /// <param name="sqlDateTime">When</param>  
        /// <param name="calendarName">The short name of the desired calendar</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = true, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromSqlDateTimeAndCalendar(SqlDateTime sqlDateTime, string calendarName)  
        {  
            return new CADateTime(sqlDateTime.Value, CalendarInfo.GetCalendarId(calendarName));  
        }  
  
        /// <summary>  
        /// Create a new CADateTime from the year/month/day  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromYearMonthDay(int year, int month, int day)  
        {  
            return new CADateTime(year, month, day);  
        }  
  
        public static SqlBoolean operator ==(CADateTime xCADateTime, CADateTime yCADateTime)  
        {  
            if (xCADateTime.IsNull || yCADateTime.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADateTime.DateTime == yCADateTime.DateTime;  
        }  
  
        public static SqlBoolean operator !=(CADateTime xCADateTime, CADateTime yCADateTime)  
        {  
            if (xCADateTime.IsNull || yCADateTime.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADateTime.DateTime != yCADateTime.DateTime;  
        }  
  
        /// <summary>  
        /// convert the datetime to string  
        /// </summary>  
        /// <returns></returns>  
        public override string ToString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            bool afternoon = this.Hour >= 12;  
            int twelveHour = this.Hour;  
            if (twelveHour == 0)  
            {  
                twelveHour = 12;  
            }  
            else if (twelveHour > 12)  
            {  
                twelveHour = twelveHour - 12;  
            }  
  
            return string.Format(  
                CultureInfo.CurrentCulture,  
                DateTimeFormatString(),  
                this.DayOfMonth,  
                this.Month,  
                this.Year,  
                twelveHour,  
                this.Hour,  
                this.Minute,  
                this.Second,  
                afternoon  
                    ? CultureInfo.CurrentCulture.DateTimeFormat.PMDesignator  
                    : CultureInfo.CurrentCulture.DateTimeFormat.AMDesignator);  
        }  
  
        /// <summary>  
        /// convert the datetime to string, using the specified format  
        /// </summary>  
        /// <param name="format">Format string</param>  
        /// <returns></returns>  
        public string ToGregorianStringUsingFormat(string format)  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(format, DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Return a string representation of this DateTime, in the Gregorian calendarId  
        /// </summary>  
        /// <returns></returns>  
        public string ToGregorianString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(DateTimeFormatInfo.CurrentInfo);  
        }  
  
        public bool IsValid()  
        {  
            return this.dtTicks >= 0;  
        }  
  
        /// <summary>  
        /// convert to sql datetime  
        /// </summary>  
        /// <returns></returns>  
        public SqlDateTime ToSqlDateTime()  
        {  
            return new SqlDateTime(this.DateTime);  
        }  
  
        public CADateTime AddYears(int years)  
        {  
            return new CADateTime(this.Calendar.AddYears(this.DateTime, years));  
        }  
  
        public CADateTime AddDays(int days)  
        {  
            return new CADateTime(this.Calendar.AddDays(this.DateTime, days));  
        }  
  
        public CADateTime AddMonths(int months)  
        {  
            return new CADateTime(this.Calendar.AddMonths(this.DateTime, months));  
        }  
  
        public CADateTime AddHours(int hours)  
        {  
            return new CADateTime(this.Calendar.AddHours(this.DateTime, hours));  
        }  
  
        public CADateTime AddMinutes(int minutes)  
        {  
            return new CADateTime(this.Calendar.AddMinutes(this.DateTime, minutes));  
        }  
  
        public CADateTime AddSeconds(int seconds)  
        {  
            return new CADateTime(this.Calendar.AddSeconds(this.DateTime, seconds));  
        }  
  
        public CADateTime AddMilliseconds(double millis)  
        {  
            return new CADateTime(this.Calendar.AddMilliseconds(this.DateTime, millis));  
        }  
  
        public double DiffDays(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalDays;  
        }  
  
        public double DiffHours(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalHours;  
        }  
  
        public double DiffMinutes(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalMinutes;  
        }  
  
        public double DiffSeconds(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalSeconds;  
        }  
  
        public double DiffMilliseconds(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalMilliseconds;  
        }  
  
        // Hash and comparison operators  
  
        public override int GetHashCode()  
        {  
            return this.DateTime.GetHashCode();  
        }  
  
        public override bool Equals(object obj)  
        {  
            if (!(obj is DateTime))  
            {  
                return false;  
            }  
  
            DateTime dt = (DateTime)obj;  
            return this.DateTime.Equals(dt);  
        }  
  
        public XmlSchema GetSchema()  
        {  
            StringReader sr = new StringReader(CADateTimeSchema);  
            XmlSchema schema = XmlSchema.Read(  
                sr,  
                new ValidationEventHandler(this.ValidationHandler));  
            sr.Dispose();  
  
            return schema;  
        }  
  
        public void ReadXml(XmlReader reader)  
        {  
            if (reader == null)  
            {  
                throw new ArgumentNullException("reader");  
            }  
  
            reader.MoveToContent();  
            if (reader.GetAttribute("IsNull").Equals("true"))  
            {  
                this.dtTicks = CADateTime.NullTicks;  
            }  
            else  
            {  
                string calendarName = reader.GetAttribute("Calendar");  
                Calendar requestedCalendar  
                    = CalendarInfo.Calendars[CalendarInfo.GetCalendarId(calendarName)];  
  
                this.dtTicks = (uint)new DateTime(  
                    int.Parse(reader.GetAttribute("Year"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Month"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Day"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Hour"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Minute"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Second"), CultureInfo.CurrentCulture),  
                    requestedCalendar).Ticks;  
            }  
        }  
  
        public void WriteXml(XmlWriter writer)  
        {  
            if (writer == null)  
            {  
                throw new ArgumentNullException("writer");  
            }  
  
            writer.WriteStartElement("CADate", "https://schemas.microsoft.com/sqlserver/2004/08/CADate");  
            writer.WriteAttributeString("IsNull", this.IsNull.ToString());  
  
            if (!this.IsNull)  
            {  
                writer.WriteAttributeString("Year", this.Year.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Month", this.Month.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Day", this.Day.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Calendar", Calendar.GetType().ToString());  
            }  
  
            writer.WriteEndElement();  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // day, month, and year components in a culture appropriate way.  
        private static string DateTimeFormatString()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.Append(CultureInfo.CurrentCulture.DateTimeFormat.ShortDatePattern);  
            sb.Append(" ");  
            sb.Append(CultureInfo.CurrentCulture.DateTimeFormat.LongTimePattern);  
            string cultureDatePattern = sb.ToString();  
  
            return CalendarInfo.SubstitutePositionForCharacters(datetimeChars, cultureDatePattern);  
        }  
  
        private void ValidationHandler(object sender, ValidationEventArgs args)  
        {  
            throw new ApplicationException(args.Message);  
        }  
    }  
  
```  
  
 <span data-ttu-id="ef677-142">이는 달력을 정의하는 데 필요한 `calendars.txt` 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-142">This is the file `calendars.txt` needed for defining the calendars.</span></span>  
  
```  
; the list of calendars  
; the key is the calendar ID, the value is the assembly-qualified name of the type  
NumCalendars = 9  
  
; Note, new calendars _MUST_ be added to the end of this list  
0 = System.Globalization.GregorianCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; Saudi Hijri, the business calendar for use in Saudi Arabia  
1 = System.Globalization.UmAlQuraCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; HijriCalendar   
2 = System.Globalization.HijriCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; other calendars  
3 = System.Globalization.JapaneseCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
4 = System.Globalization.JulianCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
5 = System.Globalization.KoreanCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
6 = System.Globalization.TaiwanCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
7 = System.Globalization.ThaiBuddhistCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
8 = System.Globalization.ChineseLunisolarCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; the default calendar for this culture  
DefaultCalendarID = 0  
  
```  
  
 <span data-ttu-id="ef677-143">이는 어셈블리를 배포하고 데이터베이스 내에서 변환 함수를 만드는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 설치 스크립트(`Install.sql`)입니다. 이 스크립트에서는 예제 데이터의 테이블도 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-143">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assemblies and creates the conversion functions within the database; it also crates a table of sample data.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[Sales].[SalesSummary]') AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
DROP TABLE [Sales].[SalesSummary];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADateTime')   
DROP TYPE CADateTime;  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADate')   
DROP TYPE CADate;  
GO  
  
-- If the assembly we want to add already exists, drop it.  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime')  
DROP ASSEMBLY CADateTime;  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.neutral')  
DROP ASSEMBLY [CADateTime.resources.neutral];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ar-SA')  
DROP ASSEMBLY [CADateTime.resources.ar-SA];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ja')  
DROP ASSEMBLY [CADateTime.resources.ja];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.zh-CN')  
DROP ASSEMBLY [CADateTime.resources.zh-CN];  
GO  
  
-- Add the assembly which contains the CLR methods we want to invoke on the server.  
DECLARE @SamplesPath nvarchar(1024);  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath= N'C:\MySample\'  
  
CREATE ASSEMBLY CADateTime  
FROM @SamplesPath + 'CADateTime.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.neutral]    
FROM @SamplesPath + 'CADateTime.resources.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.ar-SA]    
FROM @SamplesPath + 'CADateTime.resources.ar-SA.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.ja]    
FROM @SamplesPath + 'CADateTime.resources.ja.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.zh-CN]    
FROM @SamplesPath + 'CADateTime.resources.zh-CN.dll'  
WITH permission_set = safe;  
GO  
  
CREATE TYPE CADateTime EXTERNAL NAME CADateTime.[CADateTime];  
GO  
  
CREATE TYPE CADate EXTERNAL NAME CADateTime.[CADate];  
GO  
  
CREATE FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar]  
(  
    @D datetime,  
    @CalendarName nvarchar(128)  
)   
RETURNS CADate   
AS EXTERNAL NAME CADateTime.[CADate].FromSqlDateTimeAndCalendar;  
GO  
  
CREATE FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]  
(  
    @D datetime,  
    @CalendarName nvarchar(128)  
)   
RETURNS CADateTime  
AS EXTERNAL NAME CADateTime.[CADateTime].FromSqlDateTimeAndCalendar;  
GO  
  
SELECT SalesOrderID, [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar](OrderDate, 'GregorianCalendar') AS OrderDate, TotalDue   
INTO [Sales].[SalesSummary]  
FROM [Sales].[SalesOrderHeader];  
GO  
  
ALTER TABLE [Sales].[SalesSummary] WITH CHECK ADD   
    CONSTRAINT [PK_SalesSummary_SalesOrderID] PRIMARY KEY CLUSTERED   
    (  
        [SalesOrderID]  
    );  
GO  
  
ALTER TABLE [Sales].[SalesSummary] ADD DayOfYear AS [OrderDate].[Day] PERSISTED;  
GO  
  
CREATE INDEX IX_Sales_SalesSummary ON [Sales].[SalesSummary] (DayOfYear);  
GO  
```  
  
 <span data-ttu-id="ef677-144">이는 다양한 달력에서 함수를 실행하여 예제를 테스트하는 `test.sql`입니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-144">This is `test.sql`, which tests the sample by executing the functions on various calendars.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
SELECT CADateTime::CurrentCalendarName;  
  
-- Simple usage, create a new value from a string and print it out  
-- We're using ISO 8601 format dates as input, which are YYYY-MM-DD  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT CAST(@h as nvarchar(128)), @h.CalendarName;  
GO  
  
-- print it out in "full format"  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('F');  
GO  
  
-- print it out in a custom format  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('MMM dd yyyy');  
GO  
  
-- convert it to arabic (for testing purposes)  
DECLARE @h CADateTime;  
SET @h = CADateTime::Parse('1976-01-02');  
SELECT @h.ToString(), @h.ToGregorianStringUsingFormat('F');  
GO  
  
-- convert sql datetime to CAD and back  
DECLARE @h CADateTime;  
SET @h = CADateTime::FromSqlDateTime(GetDate());  
SELECT @h.ToString(), @h.ToSqlDateTime();  
GO  
  
-- get the current CAD, in two ways  
SELECT   CADateTime::Now.ToString(),   
    CADateTime::FromSqlDateTime(GetDate()).ToString();  
GO  
  
-- do some arithmetic  
DECLARE @h CADateTime, @d datetime;  
SET @h = CADateTime::Now; -- get the current hijri datetime  
SET @h = @h.AddDays(10); -- add ten days to it  
SET @d = GetDate(); -- current sql date  
SET @d = DateAdd(day, 10, @d); -- add ten days to the sql datetime  
-- print 'em both, should be the same  
SELECT @h.ToSqlDateTime(), @d;  
GO  
  
-- what about datepart  
DECLARE @h CADateTime;  
SET @h = CADateTime::Now; -- get the current datetime  
SELECT @h.Year as year, @h.Month as month, @h.Day as dayofyear, @h.DayOfMonth as dom;  
GO  
  
-- print the same date in four different calendars  
SELECT   
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
SELECT CADate::CurrentCalendarName;  
  
-- simple usage, create a new value from a string and print it out  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT CAST(@h as nvarchar(128)), @h.CalendarName;  
GO  
  
-- print it out in "date format"  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('d');  
GO  
  
-- print it out in a custom format  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('MMM dd yyyy');  
GO  
  
-- convert it to arabic (for testing purposes)  
DECLARE @h CADate;  
SET @h = CADate::Parse('1976-01-02');  
SELECT @h.ToString(), @h.ToGregorianStringUsingFormat('d');  
GO  
  
-- convert sql datetime to CAD and back  
DECLARE @h CADate;  
SET @h = CADate::FromSqlDateTime(GetDate());  
SELECT @h.ToString(), @h.ToSqlDateTime();  
GO  
  
-- get the current CAD, in two ways  
SELECT   CADate::Now.ToString(),   
    CADate::FromSqlDateTime(GetDate()).ToString();  
GO  
  
-- do some arithmetic  
DECLARE @h CADate, @d datetime;  
SET @h = CADate::Now; -- get the current hijri datetime  
SET @h = @h.AddDays(10); -- add ten days to it  
SET @d = GetDate(); -- current sql date  
SET @d = DateAdd(day, 10, @d); -- add ten days to the sql datetime  
-- print 'em both, should be the same  
SELECT @h.ToSqlDateTime(), @d;  
GO  
  
-- what about datepart  
DECLARE @h CADate;  
SET @h = CADate::Now; -- get the current datetime  
SELECT @h.Year as year, @h.Month as month, @h.Day as dayofyear, @h.DayOfMonth as dom;  
GO  
  
-- print the same date in four different calendars  
SELECT   
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
-- Show the total sales figures for particular days of the year over a 90 day   
-- range starting with day 90.  
SELECT DayOfYear, SUM(TotalDue)  
FROM [Sales].[SalesSummary]  
WHERE DayOfYear >= 90 AND DayOfYear < 180  
GROUP BY DayOfYear  
ORDER BY DayOfYear;  
GO  
  
-- Show the first day of the year where there is sales between day 90 and day 180.  
SELECT TOP 1 DayOfYear   
FROM [Sales].[SalesSummary]  
WHERE DayOfYear >= 90 AND DayOfYear < 180   
ORDER BY DayOfYear ASC  
GO  
  
SET LANGUAGE French  
GO  
  
-- print the same date in four different calendars using the French culture  
SELECT   
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
SET LANGUAGE us_english  
GO  
```  
  
 <span data-ttu-id="ef677-145">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]은 데이터베이스에서 어셈블리, 함수 및 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ef677-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assemblies, functions and table from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[Sales].[SalesSummary]') AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
DROP TABLE [Sales].[SalesSummary];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADateTime')   
DROP TYPE CADateTime;  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADate')   
DROP TYPE CADate;  
GO  
  
-- If the assembly we want to add already exists, drop it.  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime')  
DROP ASSEMBLY CADateTime;  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.neutral')  
DROP ASSEMBLY [CADateTime.resources.neutral];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ar-SA')  
DROP ASSEMBLY [CADateTime.resources.ar-SA];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ja')  
DROP ASSEMBLY [CADateTime.resources.ja];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.zh-CN')  
DROP ASSEMBLY [CADateTime.resources.zh-CN];  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef677-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef677-146">See Also</span></span>  
 [<span data-ttu-id="ef677-147">공용 언어 런타임 &#40;CLR&#41; 통합에 대한 사용 시나리오 및 예제</span><span class="sxs-lookup"><span data-stu-id="ef677-147">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  