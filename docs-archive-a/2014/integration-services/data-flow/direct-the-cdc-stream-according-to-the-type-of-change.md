---
title: 변경 유형에 따라 CDC 스트림 전송 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a9b4e0c6a196669e4cedafcecf0477b228f3001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648488"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="b9247-102">변경 유형에 따라 CDC 스트림 전송</span><span class="sxs-lookup"><span data-stu-id="b9247-102">Direct the CDC Stream According to the Type of Change</span></span>
  <span data-ttu-id="b9247-103">CDC 분할자 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 CDC 원본이 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-103">To add and configure a CDC splitter Transformation, the package must contain at least one Data Flow task and a CDC source.</span></span>  
  
 <span data-ttu-id="b9247-104">패키지에 추가되는 CDC 원본에는 NetCDC 처리 모드가 선택되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-104">The CDC source added to the package must have a NetCDC processing mode selected.</span></span> <span data-ttu-id="b9247-105">처리 모드 선택에 대한 자세한 내용은 [CDC 원본 편집기&#40;연결 관리자 페이지&#41;](../cdc-source-editor-connection-manager-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9247-105">For more information on selecting processing modes, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="b9247-106">변경 유형에 따라 CDC 스트림을 전송하려면</span><span class="sxs-lookup"><span data-stu-id="b9247-106">To direct the CDC stream according to the type of change</span></span>  
  
1.  <span data-ttu-id="b9247-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b9247-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b9247-109">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 CDC 분할자를 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC splitter to the design surface.</span></span>  
  
4.  <span data-ttu-id="b9247-110">패키지에 포함된 CDC 원본을 CDC 분할자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-110">Connect the CDC source that is included in the package to the CDC Splitter.</span></span>  
  
5.  <span data-ttu-id="b9247-111">하나 이상의 대상에 CDC 분할자를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-111">Connect the CDC splitter to one or more destinations.</span></span> <span data-ttu-id="b9247-112">최대 3개의 다른 출력을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-112">You can connect up to three different outputs.</span></span>  
  
6.  <span data-ttu-id="b9247-113">다음 출력 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-113">Select one of the following outputs:</span></span>  
  
    -   <span data-ttu-id="b9247-114">삭제 출력: 삭제 변경 행이 전송되는 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-114">Delete output: The output where DELETE change rows are directed.</span></span>  
  
    -   <span data-ttu-id="b9247-115">삽입 출력: 삽입 변경 행이 전송되는 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-115">Insert output: The output where INSERT change rows are directed.</span></span>  
  
    -   <span data-ttu-id="b9247-116">업데이트 출력: 업데이트 전/후 변경 행 및 병합 변경 행이 전송되는 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-116">Update output: The output where before/after UPDATE change rows and Merge change rows are directed.</span></span>  
  
7.  <span data-ttu-id="b9247-117">필요에 따라 **고급 편집기** 대화 상자를 사용하여 고급 속성을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-117">Optionally, you can configure the advanced properties using the **Advanced Editor** dialog box.</span></span>  
  
     <span data-ttu-id="b9247-118">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-118">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
     <span data-ttu-id="b9247-119">**고급 편집기** 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="b9247-119">To open the **Advanced Editor** dialog box:</span></span>  
  
    -   <span data-ttu-id="b9247-120">**프로젝트의** 데이터 흐름 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 화면에서 CDC 분할자를 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9247-120">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
     <span data-ttu-id="b9247-121">CDC 분할자 사용에 대한 자세한 내용은 Microsoft SQL Server Integration Services용 CDC 구성 요소를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9247-121">For more information about using the CDC splitter see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9247-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9247-122">See Also</span></span>  
 [<span data-ttu-id="b9247-123">CDC 분할자</span><span class="sxs-lookup"><span data-stu-id="b9247-123">CDC Splitter</span></span>](cdc-splitter.md)  
  
  
