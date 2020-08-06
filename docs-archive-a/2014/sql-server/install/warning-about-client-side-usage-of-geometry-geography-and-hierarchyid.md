---
title: GEOMETRY, GEOGRAPHY 및 HIERARCHYID의 클라이언트 쪽 사용에 대 한 경고 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 66898aa056800c0a7573b5afa73762785706ff7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650404"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a><span data-ttu-id="3a870-102">GEOMETRY, GEOGRAPHY 및 HIERARCHYID의 클라이언트 쪽 사용에 대한 경고</span><span class="sxs-lookup"><span data-stu-id="3a870-102">Warning about client side usage of GEOMETRY, GEOGRAPHY and HIERARCHYID</span></span>
  <span data-ttu-id="3a870-103">공간 데이터 형식을 포함하는 **Microsoft.SqlServer.Types.dll**어셈블리가 버전 10.0에서 버전 11.0으로 업그레이드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-103">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="3a870-104">이 어셈블리를 참조하는 사용자 지정 애플리케이션에서는 특정 조건에 해당될 때 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-104">Custom applications that reference this assembly may fail when certain conditions are true.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3a870-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3a870-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="3a870-106">Description</span><span class="sxs-lookup"><span data-stu-id="3a870-106">Description</span></span>  
 <span data-ttu-id="3a870-107">공간 데이터 형식을 포함하는 **Microsoft.SqlServer.Types.dll**어셈블리가 버전 10.0에서 버전 11.0으로 업그레이드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-107">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="3a870-108">이 어셈블리를 참조하는 사용자 지정 애플리케이션에서는 다음 조건에 해당될 때 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-108">Custom applications that reference this assembly may fail when the following conditions are true.</span></span>  
  
-   <span data-ttu-id="3a870-109">가 설치 된 컴퓨터에가 설치 되어 있는 컴퓨터에서 사용자 지정 응용 프로그램을 이동 하는 경우 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **SqlTypes** 어셈블리의 참조 된 버전 10.0이 없기 때문에 응용 프로그램이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-109">When you move a custom application from a computer on which [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] was installed to a computer on which only [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed, the application will fail because the referenced version 10.0 of the **SqlTypes** assembly is not present.</span></span> <span data-ttu-id="3a870-110">`"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`라는 오류 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-110">You may see this error message: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span></span>  
  
-   <span data-ttu-id="3a870-111">**SqlTypes** 어셈블리 버전 11.0을 참조 하 고 버전 10.0도 설치 되 면 다음 오류 메시지가 표시 될 수 있습니다.`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span><span class="sxs-lookup"><span data-stu-id="3a870-111">When you reference the **SqlTypes** assembly version 11.0, and version 10.0 is also installed, you may see this error message: `"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span></span>  
  
-   <span data-ttu-id="3a870-112">.NET 3.5, 4 또는 4.5를 대상으로 하는 사용자 지정 애플리케이션에서 **SqlTypes** 어셈블리 버전 11.0을 참조하는 경우 SqlClient는 기본적으로 이 어셈블리의 버전 10.0을 로드하므로 애플리케이션 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-112">When you reference the **SqlTypes** assembly version 11.0 from a custom application that targets .NET 3.5, 4, or 4.5, the application will fail because SqlClient by design loads version 10.0 of the assembly.</span></span> <span data-ttu-id="3a870-113">이 오류는 애플리케이션이 다음 메서드 중 하나를 호출할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-113">This failure occurs when the application calls one of the following methods:</span></span>  
  
    -   <span data-ttu-id="3a870-114">`GetValue` 클래스의 `SqlDataReader` 메서드</span><span class="sxs-lookup"><span data-stu-id="3a870-114">`GetValue` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="3a870-115">`GetValues` 클래스의 `SqlDataReader` 메서드</span><span class="sxs-lookup"><span data-stu-id="3a870-115">`GetValues` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="3a870-116">`SqlDataReader` 클래스의 대괄호 인덱스 연산자 []</span><span class="sxs-lookup"><span data-stu-id="3a870-116">bracket index operator [] of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="3a870-117">`ExecuteScalar` 클래스의 `SqlCommand` 메서드</span><span class="sxs-lookup"><span data-stu-id="3a870-117">`ExecuteScalar` method of the `SqlCommand` class</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3a870-118">수정 동작</span><span class="sxs-lookup"><span data-stu-id="3a870-118">Corrective Action</span></span>  
 <span data-ttu-id="3a870-119">다음 메서드 중 하나를 사용하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-119">You can work around this issue by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="3a870-120">코드에서 위에 나열된 Get 메서드 대신 다음 예와 같이 CLR `GetSqlBytes` 시스템 형식을 검색하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메서드를 호출하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-120">You can work around this issue in your code by calling the `GetSqlBytes` method, instead of the Get methods listed above, to retrieve CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system types, as shown in the following example:</span></span>  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   <span data-ttu-id="3a870-121">다음 예와 같이 애플리케이션 구성 파일에 어셈블리 리디렉션을 사용하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-121">You can work around this issue by using assembly redirection in the application configuration file, as shown in the following example:</span></span>  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   <span data-ttu-id="3a870-122">SqlClient가 어셈블리의 버전 11.0을 로드하도록 연결 문자열에서 "Type System Version" 특성에 대해 "SQL Server 2012" 값을 지정하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-122">You can work around this issue in your connection string by specifying a value of "SQL Server 2012" for the "Type System Version" attribute to force SqlClient to load version 11.0 of the assembly.</span></span> <span data-ttu-id="3a870-123">이 연결 문자열 특성은 .NET 4.5 이상에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a870-123">This connection string attribute is available only in .NET 4.5 and above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a870-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a870-124">See Also</span></span>  
 <span data-ttu-id="3a870-125">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="3a870-125">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="3a870-126">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="3a870-126">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md
)  
  
  
