---
title: SSIS를 사용하여 Excel에서 가져오기 또는 Excel로 내보내기 | Microsoft Docs
description: 필수 조건, 알려진 문제 및 제한 사항과 함께 SSIS(SQL Server Integration Services)를 사용하여 Excel 데이터 가져오거나 내보내는 방법을 알아봅니다.
ms.date: 04/10/2018
ms.prod: sql-server-2014
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58b0165925e73d0eb72b118113bc354338741a0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651104"
---
# <a name="import-data-from-excel-or-export-data-to-excel-with-sql-server-integration-services-ssis"></a><span data-ttu-id="f462f-103">SSIS(SQL Server Integration Services)를 사용하여 Excel에서 데이터 가져오기 또는 Excel로 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="f462f-103">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>

<span data-ttu-id="f462f-104">이 문서에서는 SSIS(SQL Server Integration Services)를 통해 Excel에서 데이터 가져오거나 Excel로 데이터를 내보내는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-104">This article describes how to import data from Excel or export data to Excel with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="f462f-105">또한 필수 구성 요소, 제한 사항 및 알려진 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-105">The article also describes prerequisites, limitations, and known issues.</span></span>

<span data-ttu-id="f462f-106">SSIS 패키지를 만들고 Excel 연결 관리자 및 Excel 원본 또는 Excel 대상을 사용하여 Excel에서 데이터를 가져오거나 Excel로 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-106">You can import data from Excel or export data to Excel by creating an SSIS package and using the Excel Connection Manager and the Excel Source or the Excel Destination.</span></span> <span data-ttu-id="f462f-107">또한 SSIS를 기반으로 하는 SQL Server 가져오기 및 내보내기 마법사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-107">You can also use the SQL Server Import and Export Wizard, which is built on SSIS.</span></span>

<span data-ttu-id="f462f-108">이 아티클에는 SSIS에서 Excel을 성공적으로 사용하거나 일반적인 문제를 이해하고 해결하는 데 필요한 세 가지 정보 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-108">This article contains the three sets of information you need to use Excel successfully from SSIS or to understand and troubleshoot common problems:</span></span>
1.  <span data-ttu-id="f462f-109">[필요한 파일](#files-you-need)입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-109">[The files you need](#files-you-need).</span></span>
2.  <span data-ttu-id="f462f-110">Excel에서 또는 Excel로 데이터를 로드할 때 제공해야 하는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-110">The information you have to provide when you load data from or to Excel.</span></span>
    -   <span data-ttu-id="f462f-111">데이터 원본으로 [Excel을 지정](#specify-excel)합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-111">[Specify Excel](#specify-excel) as your data source.</span></span>
    -   <span data-ttu-id="f462f-112">[Excel 파일 이름 및 경로](#excel-file)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-112">Provide the [Excel file name and path](#excel-file).</span></span>
    -   <span data-ttu-id="f462f-113">[Excel 버전](#excel-version)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-113">Select the [Excel version](#excel-version).</span></span>
    -   <span data-ttu-id="f462f-114">[첫 번째 행에 열 이름을 포함](#first-row)할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-114">Specify whether the [first row contains column names](#first-row).</span></span>
    -   <span data-ttu-id="f462f-115">[데이터를 포함하는 워크시트 또는 범위](#sheets-ranges)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-115">Provide the [worksheet or range that contains the data](#sheets-ranges).</span></span>
3.  <span data-ttu-id="f462f-116">알려진 문제 및 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-116">Known issues and limitations.</span></span>
    -   <span data-ttu-id="f462f-117">[데이터 형식](#issues-types) 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-117">Issues with [data types](#issues-types).</span></span>
    -   <span data-ttu-id="f462f-118">[가져오기](#issues-importing) 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-118">Issues with [importing](#issues-importing).</span></span>
    -   <span data-ttu-id="f462f-119">[내보내기](#issues-exporting) 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-119">Issues with [exporting](#issues-exporting).</span></span>

## <a name="get-the-files-you-need-to-connect-to-excel"></a><a name="files-you-need"></a> <span data-ttu-id="f462f-120">Excel에 연결하는 데 필요한 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="f462f-120">Get the files you need to connect to Excel</span></span>

<span data-ttu-id="f462f-121">Excel에서 데이터를 가져오거나 Excel로 데이터를 내보내려면 Excel용 연결 구성 요소가 설치되어 있지 않은 경우 먼저 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-121">Before you can import data from Excel or export data to Excel, you may have to download the connectivity components for Excel if they're not already installed.</span></span> <span data-ttu-id="f462f-122">Excel용 연결 구성 요소는 기본적으로 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-122">The connectivity components for Excel are not installed by default.</span></span>

<span data-ttu-id="f462f-123">[Microsoft Access 데이터베이스 엔진 2016 재배포 가능](https://www.microsoft.com/download/details.aspx?id=54920)에서 최신 버전의 Excel용 연결 구성 요소를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-123">Download the latest version of the connectivity components for Excel here: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).</span></span>
  
<span data-ttu-id="f462f-124">최신 버전 구성 요소는 이전 버전의 Excel에서 만든 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-124">The latest version of the components can open files created by earlier versions of Excel.</span></span>

<span data-ttu-id="f462f-125">Microsoft Access 2016 *런타임*이 아닌 Access 데이터베이스 엔진 2016 *재배포 가능 패키지*를 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-125">Make sure that you download the Access Database Engine 2016 *Redistributable* and not the Microsoft Access 2016 *Runtime*.</span></span>

<span data-ttu-id="f462f-126">컴퓨터에 32비트 버전의 Office가 이미 설치되어 있는 경우 32비트 버전의 구성 요소를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-126">If the computer already has a 32-bit version of Office, then you have to install the 32-bit version of the components.</span></span> <span data-ttu-id="f462f-127">또한 32비트 모드에서 SSIS 패키지를 실행하거나 가져오기 및 내보내기 마법사의 32비트 버전을 실행하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-127">You also have to ensure that you run the SSIS package in 32-bit mode, or run the 32-bit version of the Import and Export Wizard.</span></span>

<span data-ttu-id="f462f-128">Office 365 구독이 있는 경우 설치 관리자를 실행할 때 오류 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-128">If you have an Office 365 subscription, you may see an error message when you run the installer.</span></span> <span data-ttu-id="f462f-129">오류는 Office 간편 실행 구성 요소와 함께 다운로드를 설치할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-129">The error indicates that you can't install the download side by side with Office click-to-run components.</span></span> <span data-ttu-id="f462f-130">이 오류 메시지를 무시하려면 명령 프롬프트 창을 열고 `/quiet` 스위치를 통해 다운로드한 .EXE 파일을 실행하여 자동 모드에서 설치를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-130">To bypass this error message, run the installation in quiet mode by opening a Command Prompt window and running the .EXE file that you downloaded with the `/quiet` switch.</span></span> <span data-ttu-id="f462f-131">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-131">For example:</span></span>

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

<span data-ttu-id="f462f-132">2016 재배포 가능을 설치하는 데 문제가 있는 경우 [Microsoft Access 데이터베이스 엔진 2010 재배포 가능](https://www.microsoft.com/download/details.aspx?id=13255)에서 2010 재배포 가능 패키지를 대신 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-132">If you have trouble installing the 2016 redistributable, install the 2010 redistributable instead from here: [Microsoft Access Database Engine 2010 Redistributable](https://www.microsoft.com/download/details.aspx?id=13255).</span></span> <span data-ttu-id="f462f-133">(Excel 2013용 재배포 가능 패키지는 없습니다.)</span><span class="sxs-lookup"><span data-stu-id="f462f-133">(There is no redistributable for Excel 2013.)</span></span>

## <a name="specify-excel"></a><a name="specify-excel"></a> <span data-ttu-id="f462f-134">Excel 지정</span><span class="sxs-lookup"><span data-stu-id="f462f-134">Specify Excel</span></span>

<span data-ttu-id="f462f-135">첫 번째 단계는 Excel에 연결하려 함을 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-135">The first step is to indicate that you want to connect to Excel.</span></span>

### <a name="in-ssis"></a><span data-ttu-id="f462f-136">SSIS에서</span><span class="sxs-lookup"><span data-stu-id="f462f-136">In SSIS</span></span>
<span data-ttu-id="f462f-137">SSIS에서 Excel 연결 관리자를 만들어 Excel 원본 또는 대상 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-137">In SSIS, create an Excel Connection Manager to connect to the Excel source or destination file.</span></span> <span data-ttu-id="f462f-138">다음과 같은 여러 가지 방법으로 연결 관리자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-138">There are several ways to create the connection manager:</span></span>

-   <span data-ttu-id="f462f-139">**연결 관리자** 영역에서 마우스 오른쪽 단추를 클릭하고 **새 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-139">In the **Connection Managers** area, right-click and select **New connection**.</span></span> <span data-ttu-id="f462f-140">**SSIS 연결 관리자 추가** 대화 상자에서 **EXCEL**을 선택한 다음, **추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-140">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>
 
-   <span data-ttu-id="f462f-141">**SSIS** 메뉴에서 **새 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-141">On the **SSIS** menu, select **New connection**.</span></span> <span data-ttu-id="f462f-142">**SSIS 연결 관리자 추가** 대화 상자에서 **EXCEL**을 선택한 다음, **추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-142">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>

-   <span data-ttu-id="f462f-143">동시에 **Excel 원본 편집기** 또는 **Excel 대상 편집기**의 **연결 관리자** 페이지에서 **Excel 원본** 또는 **Excel 대상**을 구성하는 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-143">Create the connection manager at the same time that you configure the **Excel Source** or the **Excel Destination** on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**.</span></span>

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="f462f-144">SQL Server 가져오기 및 내보내기 마법사에서</span><span class="sxs-lookup"><span data-stu-id="f462f-144">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="f462f-145">가져오기 및 내보내기 마법사의 **데이터 원본 선택** 또는 **대상 선택** 페이지에서 **데이터 원본** 목록의 **Microsoft Excel**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-145">In the Import and Export Wizard, on the **Choose a Data Source** or **Choose a Destination** page, select **Microsoft Excel** in the **Data source** list.</span></span>

<span data-ttu-id="f462f-146">데이터 원본의 목록에서 Excel이 표시되지 않는 경우 32비트 마법사를 실행하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-146">If you don't see Excel in the list of data sources, make sure you're running the 32-bit wizard.</span></span> <span data-ttu-id="f462f-147">Excel 연결 구성 요소는 일반적으로 32비트 파일이며 64비트 마법사에는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-147">The Excel connectivity components are typically 32-bit files and aren't visible in the 64-bit wizard.</span></span>

## <a name="excel-file-and-file-path"></a><a name="excel-file"></a> <span data-ttu-id="f462f-148">Excel 파일 및 파일 경로</span><span class="sxs-lookup"><span data-stu-id="f462f-148">Excel file and file path</span></span>

<span data-ttu-id="f462f-149">제공할 정보의 첫 번째 부분은 Excel 파일에 대한 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-149">The first piece of info to provide is the path and file name for the Excel file.</span></span> <span data-ttu-id="f462f-150">이 정보는 SSIS 패키지의 **Excel 연결 관리자 편집기**나 가져오기 및 내보내기 마법사의 **데이터 원본 선택** 또는 **대상 선택** 페이지에서 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-150">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="f462f-151">다음과 같은 형식의 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-151">Enter the path and file name in the following format:</span></span>

-   <span data-ttu-id="f462f-152">로컬 컴퓨터의 파일은 **C:\\TestData.xlsx**입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-152">For a file on the local computer, **C:\\TestData.xlsx**.</span></span>

-   <span data-ttu-id="f462f-153">네트워크 공유의 파일은 **\\\\Sales\\Data\\TestData.xlsx**입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-153">For a file on a network share, **\\\\Sales\\Data\\TestData.xlsx**.</span></span>

<span data-ttu-id="f462f-154">또는 **찾아보기**를 클릭하고 **열기** 대화 상자를 사용하여 스프레드시트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-154">Or, click **Browse** to locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f462f-155">암호로 보호된 Excel 파일에는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-155">You can't connect to a password-protected Excel file.</span></span>

## <a name="excel-version"></a><a name="excel-version"></a> <span data-ttu-id="f462f-156">Excel 버전</span><span class="sxs-lookup"><span data-stu-id="f462f-156">Excel version</span></span>

<span data-ttu-id="f462f-157">제공할 정보의 두 번째 부분은 Excel 파일의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-157">The second piece of info to provide is the version of the Excel file.</span></span> <span data-ttu-id="f462f-158">이 정보는 SSIS 패키지의 **Excel 연결 관리자 편집기**나 가져오기 및 내보내기 마법사의 **데이터 원본 선택** 또는 **대상 선택** 페이지에서 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-158">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="f462f-159">파일을 만드는 데 사용된 Microsoft Excel의 버전 또는 다른 호환 가능한 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-159">Select the version of Microsoft Excel that was used to create the file, or another compatible version.</span></span> <span data-ttu-id="f462f-160">예를 들어 2016 연결 구성 요소를 설치하는 데 문제가 있으면 2010 구성 요소를 설치하고 목록에서 **Microsoft Excel 2007-2010**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-160">For example, if you had trouble installing the 2016 connectivity components, you can install the 2010 components and select **Microsoft Excel 2007-2010** in this list.</span></span>

<span data-ttu-id="f462f-161">이전 버전의 연결 구성 요소가 설치되어 있는 경우 목록에서 최신 버전의 Excel 버전을 선택하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-161">You may not be able to select newer Excel versions in the list if you only have older versions of the connectivity components installed.</span></span> <span data-ttu-id="f462f-162">**Excel 버전** 목록에는 SSIS가 지원하는 모든 버전의 Excel이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-162">The **Excel version** list includes all the versions of Excel supported by SSIS.</span></span> <span data-ttu-id="f462f-163">이 목록에 포함되었다고 해서 필요한 구성 요소가 설치되었다는 뜻은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-163">The presence of items in this list does not indicate that the required connectivity components are installed.</span></span> <span data-ttu-id="f462f-164">예를 들어 2016 연결 구성 요소를 설치하지 않은 경우에도 **Microsoft Excel 2016**이 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-164">For example, **Microsoft Excel 2016** appears in the list even if you have not installed the 2016 connectivity components.</span></span>

## <a name="first-row-has-column-names"></a><a name="first-row"></a> <span data-ttu-id="f462f-165">첫 번째 행에 열 이름 포함</span><span class="sxs-lookup"><span data-stu-id="f462f-165">First row has column names</span></span>

<span data-ttu-id="f462f-166">Excel에서 데이터를 가져오는 경우 다음 단계는 데이터의 첫 번째 행에 열 이름을 포함할지 여부를 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-166">If you're importing data from Excel, the next step is to indicate whether the first row of the data contains column names.</span></span> <span data-ttu-id="f462f-167">이 정보는 SSIS 패키지의 **Excel 연결 관리자 편집기**나 가져오기 및 내보내기 마법사의 **데이터 원본 선택** 페이지에서 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-167">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** page of the Import and Export Wizard.</span></span>

-   <span data-ttu-id="f462f-168">원본 데이터에 열 이름이 포함되어 있지 않아 이 옵션이 비활성화되어 있는 경우 마법사는 F1, F2 등을 열 제목으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-168">If you disable this option because the source data doesn't contain column names, the wizard uses F1, F2, and so forth, as column headings.</span></span>
-   <span data-ttu-id="f462f-169">데이터에 열 이름이 포함되어 있지만 이 옵션을 비활성화한 경우 마법사는 열 이름을 데이터의 첫 번째 행으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-169">If the data contains column names, but you disable this option, the wizard imports the column names as the first row of data.</span></span>
-   <span data-ttu-id="f462f-170">데이터에 열 이름이 포함되어 있지 않은데 이 옵션을 활성화한 경우 마법사는 원본 데이터의 첫 번째 행을 열 이름으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-170">If the data does not contain column names, but you enable this option, the wizard uses the first row of source data as the column names.</span></span> <span data-ttu-id="f462f-171">이 경우 원본 데이터의 첫 번째 행은 더 이상 데이터 자체에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-171">In this case, the first row of source data is no longer included in the data itself.</span></span>

<span data-ttu-id="f462f-172">Excel에서 데이터를 내보내고 이 옵션을 활성화한 경우 내보내는 데이터의 첫 번째 행은 열 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-172">If you're exporting data from Excel, and you enable this option, the first row of exported data includes the column names.</span></span>

## <a name="worksheets-and-ranges"></a><a name="sheets-ranges"></a> <span data-ttu-id="f462f-173">워크시트 및 범위</span><span class="sxs-lookup"><span data-stu-id="f462f-173">Worksheets and ranges</span></span>

<span data-ttu-id="f462f-174">데이터에 대해 데이터 원본이나 대상으로 사용할 수 있는 Excel 개체의 유형에는 워크시트, 명명된 된 범위 또는 해당 주소로 지정한 셀의 명명되지 않은 영역, 이렇게 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-174">There are three types of Excel objects that you can use as the source or destination for your data: a worksheet, a named range, or an unnamed range of cells that you specify with its address.</span></span>

-   <span data-ttu-id="f462f-175">**워크시트.**</span><span class="sxs-lookup"><span data-stu-id="f462f-175">**Worksheet.**</span></span> <span data-ttu-id="f462f-176">워크시트를 지정하려면 시트 이름 끝에 `$` 문자를 추가하고 문자열 주위에 구분 기호를 추가합니다(예: **[Sheet1$]** ).</span><span class="sxs-lookup"><span data-stu-id="f462f-176">To specify a worksheet, append the `$` character to the end of the sheet name and add delimiters around the string - for example, **[Sheet1$]**.</span></span> <span data-ttu-id="f462f-177">또는 기존 테이블 및 뷰 목록에서 `$` 문자로 끝나는 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-177">Or, look for a name that ends with the `$` character in the list of existing tables and views.</span></span>

-   <span data-ttu-id="f462f-178">**명명된 범위.**</span><span class="sxs-lookup"><span data-stu-id="f462f-178">**Named range.**</span></span> <span data-ttu-id="f462f-179">명명된 범위를 지정하려면 범위 이름을 제공합니다(예: **MyDataRange**).</span><span class="sxs-lookup"><span data-stu-id="f462f-179">To specify a named range, provide the range name - for example, **MyDataRange**.</span></span> <span data-ttu-id="f462f-180">또는 기존 테이블 및 뷰 목록에서 `$` 문자로 끝나지 않는 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-180">Or, look for a name that does not end with the `$` character in the list of existing tables and views.</span></span>
    
-   <span data-ttu-id="f462f-181">**명명되지 않은 범위.**</span><span class="sxs-lookup"><span data-stu-id="f462f-181">**Unnamed range.**</span></span> <span data-ttu-id="f462f-182">명명하지 않은 셀의 범위를 지정하려면 시트 이름 끝에 $ 문자를 추가하고 문자열 주위에 구분 기호를 추가합니다(예: **[Sheet1$A1:B4]** ).</span><span class="sxs-lookup"><span data-stu-id="f462f-182">To specify a range of cells that you haven't named, append the $ character to the end of the sheet name, add the range specification, and add delimiters around the string - for example, **[Sheet1$A1:B4]**.</span></span>

<span data-ttu-id="f462f-183">데이터에 대해 원본 또는 대상으로 사용하려는 Excel 개체의 유형을 선택하거나 지정하려면 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-183">To select or specify the type of Excel object that you want to use as the source or destination for your data, do one of the following things:</span></span>

### <a name="in-ssis"></a><span data-ttu-id="f462f-184">SSIS에서</span><span class="sxs-lookup"><span data-stu-id="f462f-184">In SSIS</span></span>

<span data-ttu-id="f462f-185">SSIS에서 **Excel 원본 편집기** 또는 **Excel 대상 편집기**의 **연결 관리자** 페이지에서 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-185">In SSIS, on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**, do one of the following things:</span></span>

-   <span data-ttu-id="f462f-186">**워크시트** 또는 **명명된 범위**를 사용하려면 **테이블 또는 뷰**를 **데이터 액세스 모드**로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-186">To use a **worksheet** or a **named range**, select **Table or view** as the **Data access mode**.</span></span> <span data-ttu-id="f462f-187">그런 다음, **Excel 시트의 이름** 목록에서 워크시트 또는 명명된 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-187">Then, in the **Name of the Excel sheet** list, select the worksheet or named range.</span></span>

-   <span data-ttu-id="f462f-188">해당 주소를 사용하여 지정한 **명명되지 않은 범위**를 사용하려면 **SQL 명령**을 **데이터 액세스 모드**로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-188">To use an **unnamed range** that you specify with its address, select **SQL command** as the **Data access mode**.</span></span> <span data-ttu-id="f462f-189">그런 다음, **SQL 명령 텍스트** 필드에 다음 예제와 같은 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-189">Then, in the **SQL command text** field, enter a query like the following example:</span></span>

    ```sql
    SELECT * FROM [Sheet1$A1:B5]
    ```

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="f462f-190">SQL Server 가져오기 및 내보내기 마법사에서</span><span class="sxs-lookup"><span data-stu-id="f462f-190">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="f462f-191">가져오기 및 내보내기 마법사에서 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-191">In the Import and Export Wizard, do one of the following things:</span></span>

-   <span data-ttu-id="f462f-192">Excel에서 **가져올** 경우 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-192">When you're **importing** from Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="f462f-193">**워크시트** 또는 **명명된 범위**를 사용하려면 **테이블 복사 또는 쿼리 지정** 페이지에서 **하나 이상의 테이블 또는 뷰에서 데이터 복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-193">To use a **worksheet** or a **named range**, on the **Specify table copy or query** page, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="f462f-194">그런 다음, **원본 테이블 및 뷰 선택** 페이지에 있는 **원본** 열에서 원본 워크시트 및 명명된 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-194">Then, on the **Select Source Tables and Views** page, in the **Source** column, select the source worksheets and named ranges.</span></span>

    -   <span data-ttu-id="f462f-195">해당 주소를 사용하여 지정한 **명명되지 않은 범위**를 사용하려면 **테이블 복사 또는 쿼리 지정** 페이지에서 **쿼리를 작성하여 전송할 데이터 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-195">To use an **unnamed range** that you specify with its address, on the **Specify table copy or query** page, select **Write a query to specify the data to transfer**.</span></span> <span data-ttu-id="f462f-196">그런 다음, **원본 쿼리 입력** 페이지에서 다음 예제와 비슷한 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-196">Then, on the **Provide a Source Query** page, provide a query similar to the following example:</span></span>

        ```sql
        SELECT * FROM [Sheet1$A1:B5]
        ```

-   <span data-ttu-id="f462f-197">Excel로 **내보낼** 경우 다음 작업 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-197">When you're **exporting** to Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="f462f-198">**워크시트** 또는 **명명된 범위**를 사용하려면 **원본 테이블 및 뷰 선택** 페이지에 있는 **대상** 열에서 대상 워크시트 및 명명된 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-198">To use a **worksheet** or a **named range**, on the **Select Source Tables and Views** page, in the **Destination** column, select the destination worksheets and named ranges.</span></span>

    -   <span data-ttu-id="f462f-199">해당 주소를 사용하여 지정한 **명명되지 않은 범위**를 사용하려면 **원본 테이블 및 뷰 선택** 페이지에 있는 **대상** 열에서 구분 기호 없이 다음 형식으로 범위를 입력합니다. `Sheet1$A1:B5`</span><span class="sxs-lookup"><span data-stu-id="f462f-199">To use an **unnamed range** that you specify with its address, on the **Select Source Tables and Views** page, in the **Destination** column, enter the range in the following format without delimiters: `Sheet1$A1:B5`.</span></span> <span data-ttu-id="f462f-200">마법사에서 구분 기호를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-200">The wizard adds the delimiters.</span></span>

<span data-ttu-id="f462f-201">가져오거나 내보낼 Excel 개체를 선택하거나 입력한 후에, 마법사의 **원본 테이블 및 뷰 선택** 페이지에서 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-201">After you select or enter the Excel objects to import or export, you can also do the following things on the **Select Source Tables and Views** page of the wizard:</span></span>

-   <span data-ttu-id="f462f-202">**매핑 편집**을 선택하여 원본과 대상 간에 열 매핑을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-202">Review column mappings between source and destination by selecting **Edit Mappings**.</span></span>

-   <span data-ttu-id="f462f-203">**미리 보기**를 선택하여 예상 대로 표시되는지 샘플 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-203">Preview sample data to make sure it's what you expect by selecting **Preview**.</span></span>

## <a name="issues-with-data-types"></a><a name="issues-types"></a> <span data-ttu-id="f462f-204">데이터 형식 문제</span><span class="sxs-lookup"><span data-stu-id="f462f-204">Issues with data types</span></span>

### <a name="data-types"></a><span data-ttu-id="f462f-205">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f462f-205">Data types</span></span>

<span data-ttu-id="f462f-206">Excel 드라이버는 제한된 데이터 형식 집합만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-206">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="f462f-207">예를 들어 모든 숫자 열은 double(DT_R8)로 해석되고 모든 문자열 열(메모 열 제외)은 255자 유니코드 문자열(DT_WSTR)로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-207">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> <span data-ttu-id="f462f-208">SSIS에서는 Excel 데이터 형식을 다음과 같이 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-208">SSIS maps the Excel data types as follows:</span></span>

-   <span data-ttu-id="f462f-209">숫자 - 배정밀도 부동 소수점 수(DT_R8)</span><span class="sxs-lookup"><span data-stu-id="f462f-209">Numeric - double-precision float (DT_R8)</span></span>

-   <span data-ttu-id="f462f-210">통화 - currency(DT_CY)</span><span class="sxs-lookup"><span data-stu-id="f462f-210">Currency - currency (DT_CY)</span></span>

-   <span data-ttu-id="f462f-211">부울 - Boolean(DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="f462f-211">Boolean - Boolean (DT_BOOL)</span></span>

-   <span data-ttu-id="f462f-212">날짜/시간 - datetime(DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="f462f-212">Date/time - datetime (DT_DATE)</span></span>

-   <span data-ttu-id="f462f-213">문자열 - 길이가 255인 유니코드 문자열(DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="f462f-213">String - Unicode string, length 255 (DT_WSTR)</span></span>

-   <span data-ttu-id="f462f-214">메모 - 유니코드 텍스트 스트림(DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="f462f-214">Memo - Unicode text stream (DT_NTEXT)</span></span>

### <a name="data-type-and-length-conversions"></a><span data-ttu-id="f462f-215">데이터 형식 및 길이 변환</span><span class="sxs-lookup"><span data-stu-id="f462f-215">Data type and length conversions</span></span>

<span data-ttu-id="f462f-216">SSIS에서는 데이터 형식을 암시적으로 변환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-216">SSIS does not implicitly convert data types.</span></span> <span data-ttu-id="f462f-217">따라서 파생 열 전환이나 데이터 변환을 사용하여 Excel 데이터를 비 Excel 대상으로 로드하기 전에 명시적으로 변환하거나 비 Excel 데이터를 Excel 대상으로 로드하기 전에 변환해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-217">As a result, you may have to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a destination other than Excel, or to convert data from a source other than Excel before loading it into an Excel destination.</span></span>

<span data-ttu-id="f462f-218">필요할 수 있는 일부 변환 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-218">Here are some examples of the conversions that may be required:</span></span>  
  
-   <span data-ttu-id="f462f-219">유니코드 Excel 문자열 열과 특정 코드 페이지가 있는 비유니코드 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="f462f-219">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepage.</span></span>
  
-   <span data-ttu-id="f462f-220">255자 Excel 문자열 열과 길이가 다른 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="f462f-220">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>
  
-   <span data-ttu-id="f462f-221">배정밀도 Excel 숫자 열과 다른 유형의 숫자 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="f462f-221">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>

> [!TIP]
> <span data-ttu-id="f462f-222">가져오기 및 내보내기 마법사를 사용하고 이러한 변환의 일부가 필요한 데이터의 경우 마법사에서 필요한 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-222">If you're using the Import and Export Wizard, and your data requires some of these conversions, the wizard configures the necessary conversions for you.</span></span> <span data-ttu-id="f462f-223">결과적으로, SSIS 패키지를 사용하려는 경우에도 가져오기 및 내보내기 마법사를 사용하여 초기 패키지를 만드는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-223">As a result, even when you want to use an SSIS package, it may be useful to create the initial package by using the Import and Export Wizard.</span></span> <span data-ttu-id="f462f-224">마법사에서 사용자를 위해 연결 관리자, 원본, 변환 및 대상을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-224">Let the wizard create and configure connection managers, sources, transformations, and destinations for you.</span></span>

## <a name="issues-with-importing"></a><a name="issues-importing"></a> <span data-ttu-id="f462f-225">가져오기 문제</span><span class="sxs-lookup"><span data-stu-id="f462f-225">Issues with importing</span></span>

### <a name="empty-rows"></a><span data-ttu-id="f462f-226">빈 행</span><span class="sxs-lookup"><span data-stu-id="f462f-226">Empty rows</span></span>

<span data-ttu-id="f462f-227">워크시트 또는 명명된 범위를 원본으로 지정하면 드라이버는 워크시트 또는 범위의 가장 왼쪽에서 비어 있지 않은 첫 번째 셀부터 *인접한* 블록의 셀을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-227">When you specify a worksheet or a named range as the source, the driver reads the *contiguous* block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="f462f-228">결과적으로, 데이터가 행 1에서 시작하지 않아도 되지만 원본 데이터에 빈 행을 둘 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-228">As a result, your data doesn't have to start in row 1, but you can't have empty rows in the source data.</span></span> <span data-ttu-id="f462f-229">예를 들어 열 제목과 데이터 행 사이에 빈 행을 두거나 워크시트의 맨 위에서 제목 뒤에 빈 행을 둘 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-229">For example, you can't have an empty row between the column headers and the data rows, or a title followed by empty rows at the top of the worksheet.</span></span>

<span data-ttu-id="f462f-230">데이터 위에 행이 빈 경우 워크시트로 데이터를 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-230">If there are empty rows above your data, you can't query the data as a worksheet.</span></span> <span data-ttu-id="f462f-231">Excel에서 데이터의 범위를 선택하고 범위에 이름을 할당한 다음, 워크시트 대신 명명된 범위를 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-231">In Excel, you have to select your range of data and assign a name to the range, and then query the named range instead of the worksheet.</span></span>

### <a name="missing-values"></a><span data-ttu-id="f462f-232">누락된 값</span><span class="sxs-lookup"><span data-stu-id="f462f-232">Missing values</span></span>

<span data-ttu-id="f462f-233">Excel 드라이버는 지정한 원본에서 특정 개수의 행(기본값: 8행)을 읽어 각 열의 데이터 형식을 추측합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-233">The Excel driver reads a certain number of rows (by default, eight rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="f462f-234">열에 혼합된 데이터 형식, 특히 숫자 데이터와 텍스트 데이터가 혼합되어 있으면 드라이버는 주로 사용된 데이터 형식을 지정하고 다른 형식의 데이터가 포함된 셀에 Null 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-234">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="f462f-235">사용된 횟수가 같은 경우에는 숫자 유형이 적용됩니다. Excel 워크시트에서 대부분의 셀 서식 옵션은 이러한 데이터 형식 결정에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-235">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span>

<span data-ttu-id="f462f-236">모든 값을 텍스트로 가져오도록 가져오기 모드를 지정하여 Excel 드라이버의 이러한 동작을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-236">You can modify this behavior of the Excel driver by specifying Import Mode to import all values as text.</span></span> <span data-ttu-id="f462f-237">가져오기 모드를 지정하려면 속성 창에서 Excel 연결 관리자의 연결 문자열에 있는 **확장 속성** 값에 `IMEX=1`을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-237">To specify Import Mode, add `IMEX=1` to the value of **Extended Properties** in the connection string of the Excel connection manager in the Properties window.</span></span> 

### <a name="truncated-text"></a><span data-ttu-id="f462f-238">잘린 텍스트</span><span class="sxs-lookup"><span data-stu-id="f462f-238">Truncated text</span></span>

<span data-ttu-id="f462f-239">Excel 열에 텍스트 데이터가 포함되어 있음이 확인되면 드라이버는 샘플링하는 값 중 가장 긴 값을 기준으로 데이터 형식(문자열 또는 메모)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-239">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="f462f-240">샘플링하는 행에서 255자보다 긴 값이 검색되지 않으면 이 드라이버는 해당 열을 메모 열이 아닌 255자 문자열 열로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-240">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="f462f-241">따라서 255자보다 긴 값은 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-241">Therefore, values longer than 255 characters may be truncated.</span></span>

<span data-ttu-id="f462f-242">잘림 없이 메모 열에서 데이터를 가져오려면 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-242">To import data from a memo column without truncation, you have two options:</span></span>

-   <span data-ttu-id="f462f-243">샘플링된 행 중 하나 이상의 메모 열에 255자보다 긴 값이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-243">Make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters</span></span>

-   <span data-ttu-id="f462f-244">이러한 행을 포함하도록 드라이버에서 샘플링된 행 수를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-244">Increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="f462f-245">다음과 같은 레지스트리 키에서 **TypeGuessRows** 값을 늘려 샘플링할 행 수를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-245">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the following registry key:</span></span>

| <span data-ttu-id="f462f-246">재배포 가능 구성 요소 버전</span><span class="sxs-lookup"><span data-stu-id="f462f-246">Redistributable components version</span></span> | <span data-ttu-id="f462f-247">레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="f462f-247">Registry key</span></span> |
|---|---|
| <span data-ttu-id="f462f-248">Excel 2016</span><span class="sxs-lookup"><span data-stu-id="f462f-248">Excel 2016</span></span> | <span data-ttu-id="f462f-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="f462f-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span></span> |
| <span data-ttu-id="f462f-250">Excel 2010</span><span class="sxs-lookup"><span data-stu-id="f462f-250">Excel 2010</span></span> | <span data-ttu-id="f462f-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="f462f-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span></span> |
| | |

## <a name="issues-with-exporting"></a><a name="issues-exporting"></a> <span data-ttu-id="f462f-252">내보내기 문제</span><span class="sxs-lookup"><span data-stu-id="f462f-252">Issues with exporting</span></span>

### <a name="create-a-new-destination-file"></a><span data-ttu-id="f462f-253">새 대상 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="f462f-253">Create a new destination file</span></span>

#### <a name="in-ssis"></a><span data-ttu-id="f462f-254">SSIS에서</span><span class="sxs-lookup"><span data-stu-id="f462f-254">In SSIS</span></span>

<span data-ttu-id="f462f-255">만들려는 새 Excel 파일의 경로 및 파일 이름으로 Excel 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-255">Create an Excel Connection Manager with the path and file name of the new Excel file that you want to create.</span></span> <span data-ttu-id="f462f-256">그런 다음, **Excel 대상 편집기**에서 **Excel 시트의 이름**에 대해 **새로 만들기**를 선택하여 대상 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-256">Then, in the **Excel Destination Editor**, for **Name of the Excel sheet**, select **New** to create the destination worksheet.</span></span> <span data-ttu-id="f462f-257">이 시점에서 SSIS는 지정된 워크시트를 사용하여 새 Excel 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-257">At this point, SSIS creates the new Excel file with the specified worksheet.</span></span>

#### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="f462f-258">SQL Server 가져오기 및 내보내기 마법사에서</span><span class="sxs-lookup"><span data-stu-id="f462f-258">In the SQL Server Import and Export Wizard</span></span>

<span data-ttu-id="f462f-259">**대상 선택** 페이지에서 **찾아보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-259">On the **Choose a Destination** page, select **Browse**.</span></span> <span data-ttu-id="f462f-260">**열기** 대화 상자에서 새 Excel 파일을 만들 폴더로 이동하고, 새 파일에 사용할 이름을 입력한 다음, **열기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-260">In the **Open** dialog box, navigate to the folder where you want the new Excel file to be created, provide a name for the new file, and then select **Open**.</span></span>

### <a name="export-to-a-large-enough-range"></a><span data-ttu-id="f462f-261">충분히 큰 범위로 내보내기</span><span class="sxs-lookup"><span data-stu-id="f462f-261">Export to a large enough range</span></span>

<span data-ttu-id="f462f-262">대상으로 범위를 지정하는 경우 범위가 원본 데이터의 *열 수*보다 적으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-262">When you specify a range as the destination, an error occurs if the range has fewer *columns* than the source data.</span></span> <span data-ttu-id="f462f-263">단, 지정하는 범위가 원본 데이터의 *행 수*보다 적은 경우에는 마법사에서 오류 없이 행 쓰기를 계속하고 범위 정의를 새 행 수와 일치하도록 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-263">However, if the range that you specify has fewer *rows* than the source data, the wizard continues writing rows without error and extends the range definition to match the new number of rows.</span></span>

### <a name="export-long-text-values"></a><span data-ttu-id="f462f-264">긴 텍스트 값 내보내기</span><span class="sxs-lookup"><span data-stu-id="f462f-264">Export long text values</span></span>

<span data-ttu-id="f462f-265">255자보다 긴 문자열을 Excel 열에 저장하려면 드라이버에서 대상 열의 데이터 형식을 **string** 이 아닌 **memo**로 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-265">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span>

-   <span data-ttu-id="f462f-266">기존 대상 테이블에 이미 데이터 행이 포함된 경우 드라이버에서 샘플링하는 처음 몇 개 행의 메모 열에 255자보다 긴 값의 인스턴스가 하나 이상 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-266">If an existing destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span>

-   <span data-ttu-id="f462f-267">패키지를 디자인하는 동안, 런타임 시 또는 가져오기 및 내보내기 마법사에 의해 새 대상 테이블을 만드는 경우 `CREATE TABLE` 문은 대상 메모 열의 데이터 형식으로 LONGTEXT(또는 해당 동의어 중 하나)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-267">If a new destination table is created during package design or at run time or by the Import and Export Wizard, then the `CREATE TABLE` statement must use LONGTEXT (or one of its synonyms) as the data type of the destination memo column.</span></span> <span data-ttu-id="f462f-268">마법사에서 필요한 경우 **열 매핑** 페이지의 **대상 테이블 만들기** 옵션 옆에 있는 **SQL 편집**을 클릭하여 `CREATE TABLE` 문을 확인하고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f462f-268">In the wizard, check the `CREATE TABLE` statement and revise it, if necessary, by clicking **Edit SQL** next to the **Create destination table** option on the **Column Mappings** page.</span></span>

## <a name="related-content"></a><span data-ttu-id="f462f-269">관련 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="f462f-269">Related content</span></span>

<span data-ttu-id="f462f-270">이 문서에 설명된 구성 요소와 절차에 대한 자세한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f462f-270">For more information about the components and procedures described in this article, see the following articles:</span></span>

### <a name="about-ssis"></a><span data-ttu-id="f462f-271">SSIS 정보</span><span class="sxs-lookup"><span data-stu-id="f462f-271">About SSIS</span></span>
[<span data-ttu-id="f462f-272">Excel 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="f462f-272">Excel Connection Manager</span></span>](connection-manager/excel-connection-manager.md)  
[<span data-ttu-id="f462f-273">Excel 원본</span><span class="sxs-lookup"><span data-stu-id="f462f-273">Excel Source</span></span>](data-flow/excel-source.md)  
[<span data-ttu-id="f462f-274">Excel 대상</span><span class="sxs-lookup"><span data-stu-id="f462f-274">Excel Destination</span></span>](data-flow/excel-destination.md)  
[<span data-ttu-id="f462f-275">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="f462f-275">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
[<span data-ttu-id="f462f-276">스크립트 태스크를 사용한 Excel 파일 작업</span><span class="sxs-lookup"><span data-stu-id="f462f-276">Working with Excel Files with the Script Task</span></span>](extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)

### <a name="about-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="f462f-277">SQL Server 가져오기 및 내보내기 마법사 정보</span><span class="sxs-lookup"><span data-stu-id="f462f-277">About the SQL Server Import and Export Wizard</span></span>
[<span data-ttu-id="f462f-278">Excel 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="f462f-278">Connect to an Excel Data Source</span></span>](/sql/integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard)  
[<span data-ttu-id="f462f-279">가져오기 및 내보내기 마법사의 이 간단한 예제로 시작</span><span class="sxs-lookup"><span data-stu-id="f462f-279">Get started with this simple example of the Import and Export Wizard</span></span>](/sql/integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard)

### <a name="other-articles"></a><span data-ttu-id="f462f-280">기타 문서</span><span class="sxs-lookup"><span data-stu-id="f462f-280">Other articles</span></span>
[<span data-ttu-id="f462f-281">Excel에서 SQL Server 또는 Azure SQL Database로 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="f462f-281">Import data from Excel to SQL Server or Azure SQL Database</span></span>](/sql/relational-databases/import-export/import-data-from-excel-to-sql)  

