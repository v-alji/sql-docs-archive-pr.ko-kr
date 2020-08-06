---
title: ReadOnly 모드와 ReadWrite 모드 간 Analysis Services 데이터베이스 전환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 757aedd985d969f932deacf5599716078021a1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727391"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a><span data-ttu-id="828fc-102">ReadOnly 모드와 ReadWrite 모드 간 Analysis Services 데이터베이스 전환</span><span class="sxs-lookup"><span data-stu-id="828fc-102">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>
  <span data-ttu-id="828fc-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA(데이터베이스 관리자)가 테이블 형식 또는 다차원 데이터베이스의 읽기/쓰기 모드를 변경해야 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-103">There are often situations when a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to change the read/write mode of a tabular or multidimensional database.</span></span> <span data-ttu-id="828fc-104">대개 사용자 경험 개선을 위해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버의 풀에서 데이터베이스를 공유하는 것과 같은 비즈니스 요구 사항에 따라 데이터베이스의 읽기/쓰기 모드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-104">These situations are often driven by business needs, such as sharing the database among a pool of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers for a better user experience.</span></span>  
  
 <span data-ttu-id="828fc-105">데이터베이스 모드는 여러 가지 방법으로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-105">A database mode can be switched in many ways.</span></span> <span data-ttu-id="828fc-106">이 문서에서는 다음과 같은 일반적인 시나리오에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="828fc-107">대화식으로 다음을 사용 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="828fc-107">Interactively using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="828fc-108">AMO를 사용하여 프로그래밍 방식으로 이동</span><span class="sxs-lookup"><span data-stu-id="828fc-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="828fc-109">XMLA를 사용하여 스크립트로 이동</span><span class="sxs-lookup"><span data-stu-id="828fc-109">By script using XMLA</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="828fc-110">프로시저</span><span class="sxs-lookup"><span data-stu-id="828fc-110">Procedures</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a><span data-ttu-id="828fc-111">Management Studio를 사용하여 데이터베이스의 읽기/쓰기 모드를 대화식으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="828fc-111">To switch the read/write mode of a database interactively using Management Studio</span></span>  
  
1.  <span data-ttu-id="828fc-112">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 왼쪽 또는 오른쪽 창에서 전환할 데이터베이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-112">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="828fc-113">데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-113">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="828fc-114">데이터베이스 폴더를 찾은 후 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-114">Find the database folder and note the location.</span></span> <span data-ttu-id="828fc-115">빈 데이터베이스 스토리지 위치는 데이터베이스 폴더가 서버 데이터 폴더에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-115">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="828fc-116">데이터베이스를 분리하면 즉시 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 데이터베이스 위치를 찾을 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-116">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="828fc-117">데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **분리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-117">Right-click the database and select **Detach...**</span></span>  
  
4.  <span data-ttu-id="828fc-118">분리되는 데이터베이스에 암호를 할당한 후 **확인** 을 클릭하여 분리 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-118">Assign a password to the database to be detached, and then click **OK** to execute the detach command.</span></span>  
  
5.  <span data-ttu-id="828fc-119">의 왼쪽 또는 오른쪽 창에서 **데이터베이스** 폴더를 찾습니다 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="828fc-119">Locate the **Databases** folder in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
6.  <span data-ttu-id="828fc-120">**데이터베이스** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **연결** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-120">Right-click the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="828fc-121">**폴더** 입력란에 데이터베이스 폴더의 원래 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-121">In the **folder** text box, type the original location of the database folder.</span></span> <span data-ttu-id="828fc-122">또는 찾아보기 단추 (**...**)를 사용 하 여 데이터베이스 폴더를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-122">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="828fc-123">데이터베이스의 읽기/쓰기 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-123">Select the read/write mode for the database.</span></span>  
  
9. <span data-ttu-id="828fc-124">3 단계에서 사용한 암호를 입력 하 고 **확인** 을 클릭 하 여 연결 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-124">Type the password that was used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a><span data-ttu-id="828fc-125">AMO를 사용하여 데이터베이스의 읽기/쓰기 모드를 프로그래밍 방식으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="828fc-125">To switch the read/write mode to a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="828fc-126">C# 애플리케이션에 다음 예제 코드를 적용하고 표시되는 태스크를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-126">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="828fc-127">C# 애플리케이션에서 필요한 매개 변수를 사용하여 `SwitchReadWrite()` 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-127">In your C# application, invoke `SwitchReadWrite()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="828fc-128">코드를 컴파일하고 실행하여 데이터베이스를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-128">Compile and execute your code to move the database.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a><span data-ttu-id="828fc-129">XMLA를 사용하여 스크립트로 데이터베이스의 읽기/쓰기 모드를 전환하려면</span><span class="sxs-lookup"><span data-stu-id="828fc-129">To switch the read/write mode to a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="828fc-130">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 왼쪽 또는 오른쪽 창에서 전환할 데이터베이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-130">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="828fc-131">데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-131">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="828fc-132">데이터베이스 폴더를 찾은 후 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-132">Find the database folder and note the location.</span></span> <span data-ttu-id="828fc-133">빈 데이터베이스 스토리지 위치는 데이터베이스 폴더가 서버 데이터 폴더에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-133">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="828fc-134">데이터베이스를 분리하면 즉시 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 데이터베이스 위치를 찾을 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-134">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="828fc-135">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 새 XMLA 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-135">Open a new XMLA tab in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="828fc-136">다음 XMLA 스크립트 템플릿을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-136">Copy the following script template for XMLA:</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="828fc-137">`%dbName%` 은 데이터베이스 이름으로 대체하고 `%password%` 는 암호로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-137">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="828fc-138">% 문자는 템플릿의 일부이므로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-138">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="828fc-139">XMLA 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-139">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="828fc-140">다음 XMLA 스크립트 템플릿을 새 XMLA 탭에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-140">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 <span data-ttu-id="828fc-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span><span class="sxs-lookup"><span data-stu-id="828fc-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span></span>  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="828fc-142">`%dbFolder%`는 데이터베이스 폴더의 전체 UNC 경로로 대체하고 `%ReadOnlyMode%`는 해당 값(`ReadOnly` 또는 `ReadWrite`)으로, `%password%`는 암호로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-142">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="828fc-143">% 문자는 템플릿의 일부이므로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-143">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="828fc-144">XMLA 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="828fc-144">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828fc-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="828fc-145">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="828fc-146">[Microsoft.analysisservices.sharepoint.integration.dll \*입니다.](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="828fc-146">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="828fc-147">[Analysis Services 데이터베이스 연결 및 분리](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="828fc-147">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="828fc-148">[데이터베이스 저장소 위치](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="828fc-148">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="828fc-149">[데이터베이스 ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="828fc-149">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="828fc-150">[Attach 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="828fc-150">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="828fc-151">[Detach 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="828fc-151">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="828fc-152">[ReadWriteMode 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="828fc-152">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="828fc-153">DbStorageLocation 요소</span><span class="sxs-lookup"><span data-stu-id="828fc-153">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
