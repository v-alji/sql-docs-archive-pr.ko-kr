---
title: '2단계: 플랫 파일 연결 관리자 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ba3adee2422af8b2df027f55ec84366b90ddd7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651142"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a><span data-ttu-id="fd160-102">2단계: 플랫 파일 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="fd160-102">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>
  <span data-ttu-id="fd160-103">이 태스크에서는 플랫 파일 연결 관리자를 방금 작성한 패키지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-103">In this task, you add a Flat File connection manager to the package that you just created.</span></span> <span data-ttu-id="fd160-104">플랫 파일 연결 관리자를 통해 패키지가 플랫 파일에서 데이터를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-104">A Flat File connection manager enables a package to extract data from a flat file.</span></span> <span data-ttu-id="fd160-105">플랫 파일 연결 관리자를 사용하여 패키지가 플랫 파일에서 데이터를 추출할 때 적용할 열 구분 기호를 포함한 파일 형식, 파일 이름과 위치 및 로캘과 코드 페이지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-105">Using the Flat File connection manager, you can specify the file name and location, the locale and code page, and the file format, including column delimiters, to apply when the package extracts data from the flat file.</span></span> <span data-ttu-id="fd160-106">또한 개별 열의 데이터 형식을 수동으로 지정하거나 **열 유형 제안** 대화 상자를 사용하여 추출된 데이터 열을 자동으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 데이터 형식에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-106">In addition, you can manually specify the data type for the individual columns, or use the **Suggest Column Types** dialog box to automatically map the columns of extracted data to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] data types.</span></span>  
  
 <span data-ttu-id="fd160-107">작업할 파일 형식마다 새 플랫 파일 연결 관리자를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-107">You must create a new Flat File connection manager for each file format that you work with.</span></span> <span data-ttu-id="fd160-108">이 자습서에서는 데이터 형식이 정확히 일치하는 여러 플랫 파일에서 데이터를 추출하므로 패키지에 하나의 플랫 파일 연결 관리자만 추가하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-108">Because this tutorial extracts data from multiple flat files that have exactly the same data format, you will need to add and configure only one Flat File connection manager for your package.</span></span>  
  
 <span data-ttu-id="fd160-109">이 자습서에서는 플랫 파일 연결 관리자에서 다음 속성을 구성하는 과정을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-109">For this tutorial, you will configure the following properties in your Flat File connection manager:</span></span>  
  
-   <span data-ttu-id="fd160-110">**열 이름:** 플랫 파일에는 열 이름이 없으므로 플랫 파일 연결 관리자가 기본 열 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-110">**Column names:** Because the flat file does not have column names, the Flat File connection manager creates default column names.</span></span> <span data-ttu-id="fd160-111">이러한 기본 이름은 각 열이 나타내는 내용을 식별하는 데 유용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-111">These default names are not useful for identifying what each column represents.</span></span> <span data-ttu-id="fd160-112">이러한 기본 이름을 보다 유용하게 만들려면 기본 이름을 플랫 파일 데이터가 로드될 팩트 테이블과 일치하는 이름으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-112">To make these default names more useful, you need to change the default names to names that match the fact table into which the flat file data is to be loaded.</span></span>  
  
-   <span data-ttu-id="fd160-113">**데이터 매핑:** 플랫 파일 연결 관리자에서 지정하는 데이터 형식 매핑은 연결 관리자를 참조하는 모든 플랫 파일 데이터 원본 구성 요소에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-113">**Data mappings:** The data type mappings that you specify for the Flat File connection manager will be used by all flat file data source components that reference the connection manager.</span></span> <span data-ttu-id="fd160-114">플랫 파일 연결 관리자를 사용하여 데이터 형식을 수동으로 매핑하거나 **열 유형 제안** 대화 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-114">You can either manually map the data types by using the Flat File connection manager, or you can use the **Suggest Column Types** dialog box.</span></span> <span data-ttu-id="fd160-115">이 자습서에서는 **열 유형 제안** 대화 상자에 제안된 매핑을 표시한 다음 **플랫 파일 연결 관리자 편집기** 대화 상자에서 필요한 매핑을 수동으로 만드는 과정을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-115">In this tutorial, you will view the mappings suggested in the **Suggest Column Types** dialog box and then manually make the necessary mappings in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="fd160-116">플랫 파일 연결 관리자는 데이터 파일에 대한 로캘 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-116">The Flat File connection manager provides locale information about the data file.</span></span> <span data-ttu-id="fd160-117">컴퓨터가 국가별 옵션 영어 (미국)를 사용 하도록 구성 되어 있지 않은 경우 **플랫 파일 연결 관리자 편집기** 대화 상자에서 추가 속성을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-117">If your computer is not configured to use the regional option English (United States), you must set additional properties in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a><span data-ttu-id="fd160-118">SSIS 패키지에 플랫 파일 연결 관리자를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="fd160-118">To add a Flat File connection manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="fd160-119">**연결 관리자** 영역의 아무 곳이나 마우스 오른쪽 단추로 클릭한 다음 **새 플랫 파일 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-119">Right-click anywhere in the **Connection Managers** area, and then click **New Flat File Connection**.</span></span>  
  
2.  <span data-ttu-id="fd160-120">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **연결 관리자 이름**에 **Sample Flat File Source Data**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-120">In the **Flat File Connection Manager Editor** dialog box, for **Connection manager name**, type **Sample Flat File Source Data**.</span></span>  
  
3.  <span data-ttu-id="fd160-121">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-121">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="fd160-122">**열기** 대화 상자에서 컴퓨터에 있는 SampleCurrencyData.txt 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-122">In the **Open** dialog box, locate the SampleCurrencyData.txt file on your machine.</span></span>  
  
     <span data-ttu-id="fd160-123">예제 데이터는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 단원 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-123">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="fd160-124">예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-124">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="fd160-125">[Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-125">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="fd160-126">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-126">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="fd160-127">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-127">Click the  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="fd160-128">첫 번째 데이터 행 확인란에서 열 이름의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-128">Clear the Column names in the first data row checkbox.</span></span>  
  
### <a name="to-set-locale-sensitive-properties"></a><span data-ttu-id="fd160-129">로캘 구분 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="fd160-129">To set locale sensitive properties</span></span>  
  
1.  <span data-ttu-id="fd160-130">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-130">In the **Flat File Connection Manager Editor** dialog box, click **General**.</span></span>  
  
2.  <span data-ttu-id="fd160-131">**로캘** 을 영어 (미국)로 설정 하 고 **코드 페이지** 를 1252으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-131">Set **Locale** to English (United States) and **Code page** to 1252.</span></span>  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a><span data-ttu-id="fd160-132">플랫 파일 연결 관리자에서 열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="fd160-132">To rename columns in the Flat File connection manager</span></span>  
  
1.  <span data-ttu-id="fd160-133">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-133">In the **Flat File Connection Manager Editor** dialog box, click **Advanced**.</span></span>  
  
2.  <span data-ttu-id="fd160-134">속성 창에서 다음 내용을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-134">In the property pane, make the following changes:</span></span>  
  
    -   <span data-ttu-id="fd160-135">**열 0** 이름 속성을로 변경 `AverageRate` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-135">Change the **Column 0** name property to `AverageRate`.</span></span>  
  
    -   <span data-ttu-id="fd160-136">**열 1** 이름 속성을로 변경 `CurrencyID` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-136">Change the **Column 1** name property to `CurrencyID`.</span></span>  
  
    -   <span data-ttu-id="fd160-137">**열 2** 이름 속성을로 변경 `CurrencyDate` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-137">Change the **Column 2** name property to `CurrencyDate`.</span></span>  
  
    -   <span data-ttu-id="fd160-138">**열 3** 이름 속성을로 변경 `EndOfDayRate` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-138">Change the **Column 3** name property to `EndOfDayRate`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd160-139">기본적으로 4개의 열이 모두 초기에 `OutputColumnWidth`가 50인 문자열 데이터 형식 [DT_STR]로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-139">By default, all four of the columns are initially set to a string data type [DT_STR] with an `OutputColumnWidth` of 50.</span></span>  
  
### <a name="to-remap-column-data-types"></a><span data-ttu-id="fd160-140">열 데이터 형식을 다시 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="fd160-140">To remap column data types</span></span>  
  
1.  <span data-ttu-id="fd160-141">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **유형 제안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-141">In the **Flat File Connection Manager Editor** dialog box, click **Suggest Types**.</span></span>  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fd160-142">는 처음 200개의 데이터 행에 기초하여 가장 적합한 데이터 형식을 자동으로 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-142">automatically suggests the most appropriate data types based on the first 200 rows of data.</span></span> <span data-ttu-id="fd160-143">또한 이러한 제안 옵션을 변경하여 더 많거나 적은 데이터를 샘플링하거나 정수 또는 부울 데이터의 기본 데이터 형식을 지정하거나 공백을 안쪽 여백으로 문자열 열에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-143">You can also change these suggestion options to sample more or less data, to specify the default data type for integer or Boolean data, or to add spaces as padding to string columns.</span></span>  
  
     <span data-ttu-id="fd160-144">여기에서는 **열 유형 제안** 대화 상자의 옵션을 변경하지 않고 **확인** 을 클릭하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 열의 데이터 형식을 제안하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-144">For now, make no changes to the options in the **Suggest Column Types** dialog box, and click **OK** to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggest data types for columns.</span></span> <span data-ttu-id="fd160-145">이렇게 하면 **에서 제안하는 열 데이터 형식을 볼 수 있는** 플랫 파일 연결 관리자 편집기 **대화 상자의** 고급 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-145">This returns you to the **Advanced** pane of the **Flat File Connection Manager Editor** dialog box, where you can view the column data types suggested by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="fd160-146">**취소**를 클릭하면 열 메타데이터에 대한 제안이 생성되지 않고 기본 문자열(DT_STR) 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-146">(If you click **Cancel**, no suggestions are made to column metadata and the default string (DT_STR) data type is used.)</span></span>  
  
     <span data-ttu-id="fd160-147">이 자습서에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 는 SampleCurrencyData.txt 파일 데이터에 대해 다음 테이블의 두 번째 열에 표시된 데이터 형식을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-147">In this tutorial, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggests the data types shown in the second column of the following table for the data from the SampleCurrencyData.txt file.</span></span> <span data-ttu-id="fd160-148">그러나 이후 단계에서 정의할 대상 열에 필요한 데이터 형식은 다음 표의 마지막 열에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-148">However, the data types that are required for the columns in the destination, which will be defined in a later step, are shown in the last column of the following table.</span></span>  
  
    |<span data-ttu-id="fd160-149">플랫 파일 열</span><span class="sxs-lookup"><span data-stu-id="fd160-149">Flat File Column</span></span>|<span data-ttu-id="fd160-150">제안 형식</span><span class="sxs-lookup"><span data-stu-id="fd160-150">Suggested Type</span></span>|<span data-ttu-id="fd160-151">대상 열</span><span class="sxs-lookup"><span data-stu-id="fd160-151">Destination Column</span></span>|<span data-ttu-id="fd160-152">대상 유형</span><span class="sxs-lookup"><span data-stu-id="fd160-152">Destination Type</span></span>|  
    |----------------------|--------------------|------------------------|----------------------|  
    |<span data-ttu-id="fd160-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="fd160-153">AverageRate</span></span>|<span data-ttu-id="fd160-154">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="fd160-154">float [DT_R4]</span></span>|<span data-ttu-id="fd160-155">FactCurrency.AverageRate</span><span class="sxs-lookup"><span data-stu-id="fd160-155">FactCurrency.AverageRate</span></span>|<span data-ttu-id="fd160-156">float</span><span class="sxs-lookup"><span data-stu-id="fd160-156">float</span></span>|  
    |<span data-ttu-id="fd160-157">CurrencyID</span><span class="sxs-lookup"><span data-stu-id="fd160-157">CurrencyID</span></span>|<span data-ttu-id="fd160-158">string [DT_STR]</span><span class="sxs-lookup"><span data-stu-id="fd160-158">string [DT_STR]</span></span>|<span data-ttu-id="fd160-159">DimCurrency.CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="fd160-159">DimCurrency.CurrencyAlternateKey</span></span>|<span data-ttu-id="fd160-160">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="fd160-160">nchar(3)</span></span>|  
    |<span data-ttu-id="fd160-161">CurrencyDate</span><span class="sxs-lookup"><span data-stu-id="fd160-161">CurrencyDate</span></span>|<span data-ttu-id="fd160-162">date [DT_DATE]</span><span class="sxs-lookup"><span data-stu-id="fd160-162">date [DT_DATE]</span></span>|<span data-ttu-id="fd160-163">DimDate.FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="fd160-163">DimDate.FullDateAlternateKey</span></span>|<span data-ttu-id="fd160-164">date</span><span class="sxs-lookup"><span data-stu-id="fd160-164">date</span></span>|  
    |<span data-ttu-id="fd160-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="fd160-165">EndOfDayRate</span></span>|<span data-ttu-id="fd160-166">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="fd160-166">float [DT_R4]</span></span>|<span data-ttu-id="fd160-167">FactCurrency.EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="fd160-167">FactCurrency.EndOfDayRate</span></span>|<span data-ttu-id="fd160-168">float</span><span class="sxs-lookup"><span data-stu-id="fd160-168">float</span></span>|  
  
     <span data-ttu-id="fd160-169">열에 제안 된 데이터 형식이 `CurrencyID` 대상 테이블에 있는 필드의 데이터 형식과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-169">The data type suggested for the `CurrencyID` column is incompatible with the data type of the field in the destination table.</span></span> <span data-ttu-id="fd160-170">의 데이터 형식은 `DimCurrency.CurrencyAlternateKey` nchar (3) 이므로 `CurrencyID` 문자열 [DT_STR]에서 문자열 [DT_WSTR]로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-170">Because the data type of `DimCurrency.CurrencyAlternateKey` is nchar (3), `CurrencyID` must be changed from string [DT_STR] to string [DT_WSTR].</span></span> <span data-ttu-id="fd160-171">또한 필드는 `DimDate.FullDateAlternateKey` 날짜 데이터 형식으로 정의 되므로 `CurrencyDate` 날짜 [DT_Date]에서 데이터베이스 날짜 [DT_DBDATE]로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-171">Additionally, the field `DimDate.FullDateAlternateKey` is defined as a date data type; therefore, `CurrencyDate` needs to be changed from date [DT_Date] to database date [DT_DBDATE].</span></span>  
  
2.  <span data-ttu-id="fd160-172">목록에서 CurrencyID 열을 선택 하 고 속성 창에서 열의 데이터 형식을 `CurrencyID` 문자열 [DT_STR]에서 유니코드 문자열 [DT_WSTR]로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-172">In the list, select the CurrencyID column and in the property pane, change the Data Type of column `CurrencyID` from string [DT_STR] to Unicode string [DT_WSTR].</span></span>  
  
3.  <span data-ttu-id="fd160-173">속성 창에서 열의 데이터 형식을 `CurrencyDate` 날짜 [DT_DATE]에서 데이터베이스 날짜 [DT_DBDATE]로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-173">In the property pane, change the data type of column `CurrencyDate` from date [DT_DATE] to database date [DT_DBDATE].</span></span>  
  
4.  <span data-ttu-id="fd160-174">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd160-174">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fd160-175">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="fd160-175">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fd160-176">3단계: OLE DB 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="fd160-176">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="fd160-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd160-177">See Also</span></span>  
 <span data-ttu-id="fd160-178">[플랫 파일 연결 관리자](connection-manager/file-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fd160-178">[Flat File Connection Manager](connection-manager/file-connection-manager.md) </span></span>  
 [<span data-ttu-id="fd160-179">Integration Services 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="fd160-179">Integration Services Data Types</span></span>](data-flow/integration-services-data-types.md)  
  
  
