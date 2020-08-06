---
title: 데이터 변환을 사용 하 여 데이터를 다른 데이터 형식으로 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 878741717c36c18e9a069c62e86be0148272239f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652237"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a><span data-ttu-id="47561-102">데이터 변환을 사용하여 데이터를 다른 데이터 형식으로 변환</span><span class="sxs-lookup"><span data-stu-id="47561-102">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>
  <span data-ttu-id="47561-103">데이터 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-103">To add and configure a Data Conversion transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-convert-data-to-a-different-data-type"></a><span data-ttu-id="47561-104">데이터를 다른 데이터 형식으로 변환하려면</span><span class="sxs-lookup"><span data-stu-id="47561-104">To convert data to a different data type</span></span>  
  
1.  <span data-ttu-id="47561-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47561-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="47561-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47561-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="47561-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 데이터 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="47561-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Data Conversion transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="47561-108">원본이나 이전 변환에서 연결선을 데이터 변환으로 끌어서 데이터 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-108">Connect the Data Conversion transformation to the data flow by dragging a connector from the source or the previous transformation to the Data Conversion transformation.</span></span>  
  
5.  <span data-ttu-id="47561-109">데이터 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-109">Double-click the Data Conversion transformation.</span></span>  
  
6.  <span data-ttu-id="47561-110">**데이터 변환 편집기** 대화 상자의 **사용 가능한 입력 열** 테이블에서 변환하려는 데이터 형식의 열 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-110">In the **Data ConversionTransformation Editor** dialog box, in the **Available Input Columns** table, select the check box next to the columns whose data type you want to convert.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47561-111">입력 열에 여러 개의 데이터 변환을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47561-111">You can apply multiple data conversions to an input column.</span></span>  
  
7.  <span data-ttu-id="47561-112">선택적으로 **출력 별칭** 열의 기본값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-112">Optionally, modify the default values in the **Output Alias** column.</span></span>  
  
8.  <span data-ttu-id="47561-113">**데이터 형식** 목록에서 열에 사용할 새 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-113">In the **Data Type** list, select the new data type for the column.</span></span> <span data-ttu-id="47561-114">기본 데이터 형식은 입력 열의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="47561-114">The default data type is the data type of the input column.</span></span>  
  
9. <span data-ttu-id="47561-115">선택한 데이터 형식에 따라 선택적으로 **길이**, **전체 자릿수**, **소수 자릿수**및 **코드 페이지** 열에서 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-115">Optionally, depending on the selected data type, update the values in the **Length**, the **Precision**, the **Scale**, and the **Code Page** columns.</span></span>  
  
10. <span data-ttu-id="47561-116">오류 출력을 구성하려면 **오류 출력 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-116">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="47561-117">자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../../configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47561-117">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="47561-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-118">Click **OK**.</span></span>  
  
12. <span data-ttu-id="47561-119">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47561-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47561-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47561-120">See Also</span></span>  
 <span data-ttu-id="47561-121">[Data Conversion Transformation](data-conversion-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="47561-121">[Data Conversion Transformation](data-conversion-transformation.md) </span></span>  
 <span data-ttu-id="47561-122">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="47561-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="47561-123">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="47561-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="47561-124">[Integration Services 데이터 형식](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="47561-124">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 [<span data-ttu-id="47561-125">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="47561-125">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
