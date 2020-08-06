---
title: Analysis Services 데이터베이스 이동 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- moving databases [Anlysis Services]
- moving databases
- operations [Analysis Services - multidimensional data]
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd9b099ad6765d9caccb9b0af6622eb4aa77d38c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740551"
---
# <a name="move-an-analysis-services-database"></a><span data-ttu-id="ddc29-102">Analysis Services 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-102">Move an Analysis Services Database</span></span>
  <span data-ttu-id="ddc29-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA(데이터베이스 관리자)가 다차원 또는 테이블 형식 model 데이터베이스를 다른 위치로 이동해야 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to move a multidimensional or tabular model database to a different location.</span></span> <span data-ttu-id="ddc29-104">이러한 경우는 보다 나은 성능, 데이터베이스 확장에 따른 공간 확보, 또는 제품 업그레이드를 위해 데이터베이스를 다른 디스크로 이동하는 것과 같이 대부분 비즈니스 요구 사항에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span>  
  
 <span data-ttu-id="ddc29-105">데이터베이스는 여러 가지 방법으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-105">A database can be moved in many ways.</span></span> <span data-ttu-id="ddc29-106">이 문서에서는 다음과 같은 일반적인 시나리오에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="ddc29-107">SSMS를 사용하여 대화식으로 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-107">Interactively using SSMS</span></span>  
  
-   <span data-ttu-id="ddc29-108">AMO를 사용하여 프로그래밍 방식으로 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="ddc29-109">XMLA를 사용하여 스크립트로 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-109">By script using XMLA</span></span>  
  
 <span data-ttu-id="ddc29-110">모든 시나리오에서 사용자는 데이터베이스 폴더에 액세스해야 하고 파일을 원하는 최종 대상으로 이동하기 위한 방법을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-110">All scenarios require the user to access the database folder and to use a method for moving the files to the desired final destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddc29-111">암호를 할당하지 않고 데이터베이스를 분리하면 데이터베이스가 안전하지 않은 상태에 놓이게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-111">Detaching a database without assigning a password to it leaves the database in an unsecured state.</span></span> <span data-ttu-id="ddc29-112">데이터베이스에 암호를 할당하여 기밀 정보를 보호하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-112">We recommend assigning a password to the database to protect confidential information.</span></span> <span data-ttu-id="ddc29-113">또한 데이터베이스 폴더, 하위 폴더 및 파일에 각각 해당 액세스 보안을 적용하여 무단 액세스를 방지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-113">Also, the corresponding access security should be applied to the database folder, sub-folders, and files to prevent unauthorized access to them.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ddc29-114">프로시저</span><span class="sxs-lookup"><span data-stu-id="ddc29-114">Procedures</span></span>  
  
#### <a name="moving-a-database-interactively-using-ssms"></a><span data-ttu-id="ddc29-115">SSMS를 사용하여 대화식으로 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-115">Moving a database interactively using SSMS</span></span>  
  
1.  <span data-ttu-id="ddc29-116">SSMS의 왼쪽 또는 오른쪽 창에서 이동할 데이터베이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-116">Locate the database to be moved in the left or right pane of SSMS.</span></span>  
  
2.  <span data-ttu-id="ddc29-117">데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **분리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-117">Right-click on the database and select **Detach...**</span></span>  
  
3.  <span data-ttu-id="ddc29-118">분리되는 데이터베이스에 암호를 할당한 후 **확인** 을 클릭하여 분리 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-118">Assign a password to the database to be detached, then click **OK** to execute the detach command.</span></span>  
  
4.  <span data-ttu-id="ddc29-119">운영 체제 메커니즘을 사용하거나 파일 이동을 위한 각자의 표준 방법을 사용하여 데이터베이스 폴더를 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-119">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
5.  <span data-ttu-id="ddc29-120">SSMS의 왼쪽 또는 오른쪽 창에서 **데이터베이스** 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-120">Locate the **Databases** folder in the left or right pane of SSMS.</span></span>  
  
6.  <span data-ttu-id="ddc29-121">**데이터베이스** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **연결** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-121">Right-click on the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="ddc29-122">**폴더** 입력란에 데이터베이스 폴더의 새 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-122">In the **folder** text box, type the new location of the database folder.</span></span> <span data-ttu-id="ddc29-123">또는 찾아보기 단추 (**...**)를 사용 하 여 데이터베이스 폴더를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-123">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="ddc29-124">`ReadWrite`데이터베이스에 대 한 모드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-124">Select the `ReadWrite` mode for the database.</span></span>  
  
9. <span data-ttu-id="ddc29-125">3단계에 사용한 암호를 입력하고 **확인** 을 클릭하여 연결 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-125">Type the password used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="moving-a-database-programmatically-using-amo"></a><span data-ttu-id="ddc29-126">AMO를 사용하여 프로그래밍 방식으로 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-126">Moving a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="ddc29-127">C# 애플리케이션에 다음 예제 코드를 적용하고 표시되는 태스크를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-127">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="ddc29-128">C# 애플리케이션에서 필요한 매개 변수를 사용하여 `MoveDb()` 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-128">In your C# application, invoke `MoveDb()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="ddc29-129">코드를 컴파일하고 실행하여 데이터베이스를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-129">Compile and execute your code to move the database.</span></span>  
  
#### <a name="moving-a-database-by-script-using-xmla"></a><span data-ttu-id="ddc29-130">XMLA를 사용하여 스크립트로 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="ddc29-130">Moving a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="ddc29-131">SSMS에서 새 XMLA 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-131">Open a new XMLA tab in SSMS.</span></span>  
  
2.  <span data-ttu-id="ddc29-132">다음 XMLA 스크립트 템플릿을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-132">Copy the following script template for XMLA</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="ddc29-133">`%dbName%` 은 데이터베이스 이름으로 대체하고 `%password%` 는 암호로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-133">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="ddc29-134">% 문자는 템플릿의 일부이므로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-134">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="ddc29-135">XMLA 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-135">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="ddc29-136">운영 체제 메커니즘을 사용하거나 파일 이동을 위한 각자의 표준 방법을 사용하여 데이터베이스 폴더를 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-136">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
4.  <span data-ttu-id="ddc29-137">다음 XMLA 스크립트 템플릿을 새 XMLA 탭에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-137">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="ddc29-138">`%dbFolder%`는 데이터베이스 폴더의 전체 UNC 경로로 대체하고 `%ReadOnlyMode%`는 해당 값(`ReadOnly` 또는 `ReadWrite`)으로, `%password%`는 암호로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-138">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="ddc29-139">% 문자는 템플릿의 일부이므로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-139">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="ddc29-140">XMLA 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc29-140">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc29-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddc29-141">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="ddc29-142">[Microsoft.analysisservices.sharepoint.integration.dll \*입니다.](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="ddc29-142">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="ddc29-143">[Analysis Services 데이터베이스 연결 및 분리](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ddc29-143">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="ddc29-144">[데이터베이스 저장소 위치](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="ddc29-144">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="ddc29-145">[데이터베이스 ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="ddc29-145">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="ddc29-146">[Attach 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="ddc29-146">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="ddc29-147">[Detach 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="ddc29-147">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="ddc29-148">[ReadWriteMode 요소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="ddc29-148">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="ddc29-149">DbStorageLocation 요소</span><span class="sxs-lookup"><span data-stu-id="ddc29-149">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
