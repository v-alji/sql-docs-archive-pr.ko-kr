---
title: 데이터 흐름에서 구성 요소 추가 또는 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f041258d2b66e7b8da540a842848ebf70f4ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729675"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a><span data-ttu-id="2b69a-102">데이터 흐름에서 구성 요소 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="2b69a-102">Add or Delete a Component in a Data Flow</span></span>
  <span data-ttu-id="2b69a-103">데이터 흐름 구성 요소는 데이터 흐름에 있는 원본, 대상 및 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-103">Data flow components are sources, destinations, and transformations in a data flow.</span></span> <span data-ttu-id="2b69a-104">데이터 흐름에 구성 요소를 추가하려면 패키지의 제어 흐름에 데이터 흐름 태스크 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-104">Before you can add components to a data flow, the control flow in the package must include a Data Flow task.</span></span>  
  
 <span data-ttu-id="2b69a-105">다음 절차에서는 패키지의 데이터 흐름에서 구성 요소를 추가하거나 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-105">The following procedures describe how to add or delete a component in the data flow of a package.</span></span>  
  
### <a name="to-add-a-component-to-a-data-flow"></a><span data-ttu-id="2b69a-106">데이터 흐름에 구성 요소를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2b69a-106">To add a component to a data flow</span></span>  
  
1.  <span data-ttu-id="2b69a-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2b69a-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2b69a-109">**제어 흐름** 탭을 클릭한 후 구성 요소를 추가하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-109">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow to which you want to add a component.</span></span>  
  
4.  <span data-ttu-id="2b69a-110">도구 상자에서 **데이터 흐름 원본**, **데이터 흐름 변환**또는 **데이터 흐름 대상**을 확장한 후 데이터 흐름 항목을 **데이터 흐름** 탭의 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-110">In the Toolbox, expand **Data Flow Sources**, **Data Flow Transformations**, or **Data Flow Destinations**, and then drag a data flow item to the design surface of the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="2b69a-111">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-111">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-component-from-a-data-flow"></a><span data-ttu-id="2b69a-112">데이터 흐름에서 구성 요소를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2b69a-112">To delete a component from a data flow</span></span>  
  
1.  <span data-ttu-id="2b69a-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2b69a-114">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-114">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2b69a-115">**제어 흐름** 탭을 클릭한 후 구성 요소를 삭제하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-115">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow from which you want to delete a component.</span></span>  
  
4.  <span data-ttu-id="2b69a-116">데이터 흐름 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-116">Right-click the data flow component, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="2b69a-117">삭제 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-117">Confirm the delete operation.</span></span>  
  
6.  <span data-ttu-id="2b69a-118">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b69a-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b69a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b69a-119">See Also</span></span>  
 <span data-ttu-id="2b69a-120">[데이터 흐름의 구성 요소 연결](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="2b69a-120">[Connect Components in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="2b69a-121">[데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="2b69a-121">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="2b69a-122">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="2b69a-122">Data Flow</span></span>](data-flow.md)  
  
  
