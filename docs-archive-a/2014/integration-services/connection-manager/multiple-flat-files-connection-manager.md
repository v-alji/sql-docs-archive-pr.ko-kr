---
title: 다중 플랫 파일 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a17125fedb495daabc4838161b3260c0d5590319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659599"
---
# <a name="multiple-flat-files-connection-manager"></a><span data-ttu-id="01cee-102">다중 플랫 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="01cee-102">Multiple Flat Files Connection Manager</span></span>
  <span data-ttu-id="01cee-103">다중 플랫 파일 연결 관리자를 사용하면 패키지에서 다중 플랫 파일의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-103">A Multiple Flat Files connection manager enables a package to access data in multiple flat files.</span></span> <span data-ttu-id="01cee-104">예를 들어 데이터 흐름 태스크가 For 루프 컨테이너와 같은 루프 컨테이너 내부에 있는 경우 플랫 파일 원본에서 다중 플랫 파일 연결 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-104">For example, a Flat File source can use a Multiple Flat Files connection manager when the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="01cee-105">각 컨테이너 루프에서 플랫 파일 원본은 다중 플랫 파일 연결 관리자가 제공하는 다음 파일 이름에서 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-105">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span>  
  
 <span data-ttu-id="01cee-106">패키지에 다중 플랫 파일 연결 관리자를 추가 하면에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 다중 플랫 파일 연결로 확인 되는 연결 관리자를 만들고, 다중 플랫 파일 연결 관리자에 대 한 속성을 설정 하 고, 다중 플랫 파일 연결 관리자를 패키지의 컬렉션에 추가 합니다 `Connections` .</span><span class="sxs-lookup"><span data-stu-id="01cee-106">When you add a Multiple Flat Files connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Flat Files connection at run time, sets the properties on the Multiple Flat Files connection manager, and adds the Multiple Flat Files connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="01cee-107">연결 관리자의 `ConnectionManagerType` 속성이 `MULTIFLATFILE`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-107">The `ConnectionManagerType` property of the connection manager is set to `MULTIFLATFILE`.</span></span>  
  
 <span data-ttu-id="01cee-108">다음과 같은 방법으로 다중 플랫 파일 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-108">You can configure the Multiple Flat Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="01cee-109">사용할 파일, 로캘 및 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-109">Specify the files, locale, and code page to use.</span></span> <span data-ttu-id="01cee-110">로캘은 날짜 같은 로캘 구분 데이터를 해석하는 데 사용되고 코드 페이지는 문자열 데이터를 유니코드로 변환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-110">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="01cee-111">파일 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-111">Specify the file format.</span></span> <span data-ttu-id="01cee-112">구분 기호로 분리된 형식, 고정 폭 형식 또는 왼쪽 정렬 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-112">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="01cee-113">머리글 행, 데이터 행 및 열 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-113">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="01cee-114">열 구분 기호는 파일 수준에서 설정하고 열 수준에서 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-114">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="01cee-115">파일의 첫 번째 행에 열 이름이 포함되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-115">Indicate whether the first row in the files contains column names.</span></span>  
  
-   <span data-ttu-id="01cee-116">텍스트 한정자 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-116">Specify a text qualifier character.</span></span> <span data-ttu-id="01cee-117">텍스트 한정자를 인식하도록 각 열을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-117">Each column can be configured to recognize a text qualifier.</span></span>  
  
-   <span data-ttu-id="01cee-118">개별 열에 대해 이름, 데이터 형식 및 최대 너비와 같은 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-118">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="01cee-119">다중 플랫 파일 연결 관리자에서 다중 파일을 참조하는 경우 파일의 경로는 세로줄 문자(|)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-119">When the Multiple Flat Files connection manager references multiple files, the paths of the files are separated by the pipe (|) character.</span></span> <span data-ttu-id="01cee-120">연결 관리자의 `ConnectionString` 속성은 다음 형식을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-120">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="01cee-121">또한 와일드카드 문자를 사용하여 다중 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-121">You can also specify multiple files by using wildcard characters.</span></span> <span data-ttu-id="01cee-122">예를 들어 C 드라이브의 모든 텍스트 파일을 참조 하려면 속성의 값을 `ConnectionString` c: \* .txt로 설정할 수 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="01cee-122">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="01cee-123">다중 플랫 파일 연결 관리자에서 다중 파일을 참조하는 경우 모든 파일은 형식이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-123">If a Multiple Flat Files connection manager references multiple files, all the files must have the same format.</span></span>  
  
 <span data-ttu-id="01cee-124">기본적으로 다중 플랫 파일 연결 관리자는 문자열 길이를 50자로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-124">By default, the Multiple Flat Files connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="01cee-125">**다중 플랫 파일 연결 관리자 편집기** 대화 상자에서 예제 데이터를 평가하고 이러한 열의 길이를 자동으로 조정하여 데이터가 잘리지 않거나 열 너비를 초과하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-125">In the **Multiple Flat Files Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="01cee-126">플랫 파일 원본 또는 변환에서 열 길이를 조정하지 않으면 열 길이가 데이터 흐름 전체에서 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-126">Unless you resize the column length in a Flat File source or a transformation, the column length remains the same throughout the data flow.</span></span> <span data-ttu-id="01cee-127">이러한 열이 보다 좁은 대상 열에 매핑되면 사용자 인터페이스에 경고가 나타나며 런타임 시 데이터 잘림으로 인한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-127">If these columns map to destination columns that are narrower, warnings appear in the user interface, and at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="01cee-128">플랫 파일 연결 관리자, 플랫 파일 원본 또는 변환에서 대상 열과 호환 가능하도록 열 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-128">You can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="01cee-129">출력 열의 길이를 수정 하려면 `Length` **고급 편집기** 대화 상자의 **입/출력 속성** 탭에서 출력 열의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-129">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="01cee-130">연결 관리자를 사용하는 플랫 파일 원본을 추가 및 구성한 후에 다중 플랫 파일 연결 관리자에서 열 길이를 업데이트한 경우에는 플랫 파일 원본에서 출력 열의 크기를 수동으로 조정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-130">If you update column lengths in the Multiple Flat Files connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="01cee-131">**플랫 파일 원본** 대화 상자를 열면 플랫 파일 원본에 열 메타데이터를 동기화하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-131">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a><span data-ttu-id="01cee-132">다중 플랫 파일 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="01cee-132">Configuration of the Multiple Flat Files Connection Manager</span></span>  
 <span data-ttu-id="01cee-133">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="01cee-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="01cee-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="01cee-135">다중 플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="01cee-135">Multiple Flat Files Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="01cee-136">다중 플랫 파일 연결 관리자 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="01cee-136">Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [<span data-ttu-id="01cee-137">다중 플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="01cee-137">Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="01cee-138">다중 플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="01cee-138">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="01cee-139">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="01cee-139">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cee-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01cee-140">See Also</span></span>  
 <span data-ttu-id="01cee-141">[플랫 파일 원본](../data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="01cee-141">[Flat File Source](../data-flow/flat-file-source.md) </span></span>  
 <span data-ttu-id="01cee-142">[플랫 파일 대상](../data-flow/flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="01cee-142">[Flat File Destination](../data-flow/flat-file-destination.md) </span></span>  
 [<span data-ttu-id="01cee-143">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="01cee-143">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
