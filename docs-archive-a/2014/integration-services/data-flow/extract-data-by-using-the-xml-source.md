---
title: XML 원본을 사용하여 데이터 추출 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57758353c476badfba4cb12a1ef6b5101f16735d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742428"
---
# <a name="extract-data-by-using-the-xml-source"></a><span data-ttu-id="7ebc3-102">XML 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="7ebc3-102">Extract Data by Using the XML Source</span></span>
  <span data-ttu-id="7ebc3-103">XML 원본을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크가 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-103">To add and configure an XML source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-xml-source"></a><span data-ttu-id="7ebc3-104">XML 원본을 사용하여 데이터를 추출하려면</span><span class="sxs-lookup"><span data-stu-id="7ebc3-104">To extract data using an XML source</span></span>  
  
1.  <span data-ttu-id="7ebc3-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="7ebc3-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="7ebc3-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 XML 원본을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the XML source to the design surface.</span></span>  
  
4.  <span data-ttu-id="7ebc3-108">XML 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-108">Double-click the XML source.</span></span>  
  
5.  <span data-ttu-id="7ebc3-109">**XML 원본 편집기**의 **연결 관리자** 페이지에서 데이터 액세스 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-109">In the **XML Source Editor**, on the **Connection Manager** page, select a data access mode:</span></span>  
  
    -   <span data-ttu-id="7ebc3-110">**XML 파일 위치** 액세스 모드의 경우 **찾아보기** 를 클릭하여 XML 파일이 들어 있는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-110">For the **XML file location** access mode, click **Browse** and locate the folder that contains the XML file.</span></span>  
  
    -   <span data-ttu-id="7ebc3-111">**변수를 사용한 XML 파일** 액세스 모드의 경우 XML 파일의 경로가 들어 있는 사용자 정의 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-111">For the **XML file from variable** access mode, select the user-defined variable that contains the path of the XML file.</span></span>  
  
    -   <span data-ttu-id="7ebc3-112">**변수를 사용한 XML 데이터** 액세스 모드의 경우 XML 데이터가 들어 있는 사용자 정의 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-112">For the **XML data from variable** access mode, select the user-defined variable that contains the XML data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ebc3-113">XML 원본이 포함된 데이터 흐름 태스크의 범위나 패키지 범위에 변수가 정의되어 있어야 하며, 변수에 문자열 데이터 형식이 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-113">The variables must be defined in the scope of the Data Flow task that contains the XML source, or in the scope of the package; additionally, the variable must have a string data type.</span></span>  
  
6.  <span data-ttu-id="7ebc3-114">XML 문서에 스키마 정보가 포함되는 경우 선택적으로 **인라인 스키마 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-114">Optionally, select **Use inline schema** to indicate that the XML document includes schema information.</span></span>  
  
7.  <span data-ttu-id="7ebc3-115">XML 파일에 대해 외부 XSD(XML 스키마 정의 언어) 스키마를 지정하려면 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-115">To specify an external XML Schema definition language (XSD) schema for the XML file, do one of the following:</span></span>  
  
    -   <span data-ttu-id="7ebc3-116">**찾아보기** 를 클릭하여 기존 XSD 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-116">Click **Browse** to locate an existing XSD file.</span></span>  
  
    -   <span data-ttu-id="7ebc3-117">**XSD 생성** 을 클릭하여 XML 파일로부터 XSD를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-117">Click **Generate XSD** to create an XSD from the XML file.</span></span>  
  
8.  <span data-ttu-id="7ebc3-118">출력 열의 이름을 업데이트하려면 **열** 을 클릭하고 **출력 열** 목록에서 값을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-118">To update the names of output columns, click **Columns** and edit the values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="7ebc3-119">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-119">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="7ebc3-120">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-120">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="7ebc3-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-121">Click **OK**.</span></span>  
  
11. <span data-ttu-id="7ebc3-122">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ebc3-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebc3-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ebc3-123">See Also</span></span>  
 <span data-ttu-id="7ebc3-124">[XML 원본](xml-source.md) </span><span class="sxs-lookup"><span data-stu-id="7ebc3-124">[XML Source](xml-source.md) </span></span>  
 <span data-ttu-id="7ebc3-125">[Integration Services 변환](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="7ebc3-125">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="7ebc3-126">[Integration Services 경로](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="7ebc3-126">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="7ebc3-127">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="7ebc3-127">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
