---
title: 플랫 파일 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], Flat File
- connections [Integration Services], flat files
- files [Integration Services], connections
- Flat File connection manager
- flat files
- flat file connections [Integration Services]
ms.assetid: 7830f80d-af32-4e8f-a6fc-f03af6bc1946
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 961fa5ebd0c254c152cb4a84a855f719b6dfaa43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738572"
---
# <a name="flat-file-connection-manager"></a><span data-ttu-id="4978e-102">Flat File Connection Manager</span><span class="sxs-lookup"><span data-stu-id="4978e-102">Flat File Connection Manager</span></span>
  <span data-ttu-id="4978e-103">플랫 파일 연결 관리자를 사용하면 패키지에서 플랫 파일의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-103">A Flat File connection manager enables a package to access data in a flat file.</span></span> <span data-ttu-id="4978e-104">예를 들어 플랫 파일 원본 및 대상은 플랫 파일 연결 관리자를 사용하여 데이터를 추출 및 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-104">For example, the Flat File source and destination can use Flat File connection managers to extract and load data.</span></span>  
  
 <span data-ttu-id="4978e-105">플랫 파일 연결 관리자는 하나의 파일만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-105">The Flat File connection manager can access only one file.</span></span> <span data-ttu-id="4978e-106">파일을 여러 개 참조하려면 플랫 파일 연결 관리자 대신 다중 플랫 파일 연결 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4978e-106">To reference multiple files, use a Multiple Flat Files connection manager instead of a Flat File connection manager.</span></span> <span data-ttu-id="4978e-107">자세한 내용은 [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4978e-107">For more information, see [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="column-length"></a><span data-ttu-id="4978e-108">열 길이</span><span class="sxs-lookup"><span data-stu-id="4978e-108">Column Length</span></span>  
 <span data-ttu-id="4978e-109">기본적으로 플랫 파일 연결 관리자는 문자열 열의 길이를 50자로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-109">By default, the Flat File connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="4978e-110">**플랫 파일 연결 관리자 편집기** 대화 상자에서 샘플 데이터를 평가하고 이러한 열의 길이를 자동으로 조정하여 데이터가 잘리지 않거나 열 너비를 초과하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-110">In the **Flat File Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="4978e-111">또한 플랫 파일 원본 또는 변환에서 열 길이를 나중에 조정하지 않는 한 문자열 열 길이가 데이터 흐름 전체에서 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-111">Also, unless you subsequently resize the column length in a Flat File source or a transformation, the column length of string column remains the same throughout the data flow.</span></span> <span data-ttu-id="4978e-112">이러한 문자열 열이 보다 좁은 대상 열에 매핑되면 사용자 인터페이스에 경고가 나타나고</span><span class="sxs-lookup"><span data-stu-id="4978e-112">If these string columns map to destination columns that are narrower, warnings appear in the user interface.</span></span> <span data-ttu-id="4978e-113">런타임 시 데이터 잘림으로 인한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-113">Moreover, at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="4978e-114">오류나 잘림이 발생하지 않도록 하기 위해 플랫 파일 연결 관리자, 플랫 파일 원본 또는 변환에서 대상 열과 호환 가능하도록 열 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-114">To avoid errors or truncation, you can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="4978e-115">출력 열의 길이를 수정 하려면 `Length` **고급 편집기** 대화 상자의 **입/출력 속성** 탭에서 출력 열의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-115">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="4978e-116">연결 관리자를 사용하는 플랫 파일 원본을 추가 및 구성한 후에 플랫 파일 연결 관리자에서 열 길이를 업데이트한 경우에는 플랫 파일 원본에서 출력 열의 크기를 수동으로 조정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-116">If you update column lengths in the Flat File connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="4978e-117">**플랫 파일 원본** 대화 상자를 열면 플랫 파일 원본에 열 메타데이터를 동기화하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-117">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-flat-file-connection-manager"></a><span data-ttu-id="4978e-118">플랫 파일 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="4978e-118">Configuration of the Flat File Connection Manager</span></span>  
 <span data-ttu-id="4978e-119">패키지에 플랫 파일 연결 관리자를 추가 하면에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 플랫 파일 연결로 확인 되는 연결 관리자를 만들고, 플랫 파일 연결 속성을 설정 하 고, 플랫 파일 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-119">When you add a Flat File connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Flat File connection at run time, sets the Flat File connection properties, and adds the Flat File connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="4978e-120">연결 관리자의 `ConnectionManagerType` 속성이 `FLATFILE`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-120">The `ConnectionManagerType` property of the connection manager is set to `FLATFILE`.</span></span>  
  
 <span data-ttu-id="4978e-121">기본적으로 플랫 파일 연결 관리자는 따옴표로 표시되지 않은 데이터에서 항상 행 구분자를 검사하고 행 구분자를 찾으면 새 행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-121">By default, the Flat File connection manager always checks for a row delimiter in unquoted data, and starts a new row when a row delimiter is found.</span></span> <span data-ttu-id="4978e-122">그러면 연결 관리자가 열 필드가 누락된 행을 사용하여 파일을 올바르게 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-122">This enables the connection manager to correctly parse files with rows that are missing column fields.</span></span>  
  
 <span data-ttu-id="4978e-123">일부 경우에는 이 기능을 비활성화해야 패키지 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-123">In some cases, disabling this feature may improve package performance.</span></span> <span data-ttu-id="4978e-124">플랫 파일 연결 관리자 속성인 **AlwaysCheckForRowDelimiters**을로 설정 하 여이 기능을 사용 하지 않도록 설정할 수 있습니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="4978e-124">You can disable this feature by setting the Flat File connection manager property, **AlwaysCheckForRowDelimiters**, to `False`.</span></span>  
  
 <span data-ttu-id="4978e-125">다음과 같은 방법으로 플랫 파일 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-125">You can configure the Flat File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="4978e-126">사용할 파일, 로캘 및 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-126">Specify the file, locale, and code page to use.</span></span> <span data-ttu-id="4978e-127">로캘은 날짜 같은 로캘 구분 데이터를 해석하는 데 사용되고 코드 페이지는 문자열 데이터를 유니코드로 변환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-127">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="4978e-128">파일 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-128">Specify the file format.</span></span> <span data-ttu-id="4978e-129">구분 기호로 분리된 형식, 고정 폭 형식 또는 왼쪽 정렬 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-129">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="4978e-130">머리글 행, 데이터 행 및 열 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-130">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="4978e-131">열 구분 기호는 파일 수준에서 설정하고 열 수준에서 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-131">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="4978e-132">파일의 첫 번째 행에 열 이름이 포함되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-132">Indicate whether the first row in the file contains column names.</span></span>  
  
-   <span data-ttu-id="4978e-133">텍스트 한정자 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-133">Specify a text qualifier character.</span></span> <span data-ttu-id="4978e-134">텍스트 한정자를 인식하도록 각 열을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-134">Each column can be configured to recognize a text qualifier.</span></span>  
  
     <span data-ttu-id="4978e-135">한정자 문자를 사용하여 한정된 문자열에 한정자 문자를 포함하는 기능이 이제 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-135">The use of a qualifier character to embed a qualifier character into a qualified string is now supported.</span></span> <span data-ttu-id="4978e-136">텍스트 한정자가 두 번 나올 경우 해당 문자열이 한 번 나온 것처럼 리터럴로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-136">The double instance of a text qualifier is interpreted as a literal, single instance of that string.</span></span> <span data-ttu-id="4978e-137">예를 들어 텍스트 한정자가 작은따옴표이고 입력 데이터가 'abc', 'def', 'g'hi'인 경우 출력 데이터는 abc, def, g'hi입니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-137">For example, if the text qualifier is a single quote and the input data is 'abc', 'def', 'g'hi', the output data is abc, def, g'hi.</span></span>  
  
-   <span data-ttu-id="4978e-138">개별 열에 대해 이름, 데이터 형식 및 최대 너비와 같은 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-138">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="4978e-139">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 속성 창에 식을 지정하여 플랫 파일 연결 관리자에 대한 ConnectionString 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-139">You can set the ConnectionString property for the Flat File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="4978e-140">유효성 검사 오류를 방지하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-140">To avoid a validation error, do the following.</span></span>  
  
-   <span data-ttu-id="4978e-141">식을 사용해서 파일을 지정할 경우, **플랫 파일 연결 관리자 편집기** 의 **파일 이름**상자에 파일 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-141">When you use an expression to specify the file, add a file path in the **File name** box in the **Flat File Connection Manager Editor**.</span></span>  
  
-   <span data-ttu-id="4978e-142">플랫 파일 연결 관리자에서 **DelayValidation** 속성을 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-142">Set the **DelayValidation** property on the Flat File connection manager to **True**.</span></span>  
  
 <span data-ttu-id="4978e-143">플랫 파일 연결 관리자에서 플랫 파일 대상에 식을 사용하여 런타임에 파일 이름을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-143">You can use an expression to create a file name at runtime by using the Flat File connection manager with the Flat File destination.</span></span>  
  
 <span data-ttu-id="4978e-144">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-144">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4978e-145">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="4978e-145">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4978e-146">플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4978e-146">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="4978e-147">플랫 파일 연결 관리자 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4978e-147">Flat File Connection Manager Editor &#40;Columns Page&#41;</span></span>](../flat-file-connection-manager-editor-columns-page.md)  
  
-   [<span data-ttu-id="4978e-148">플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4978e-148">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="4978e-149">플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4978e-149">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="4978e-150">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4978e-150">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
