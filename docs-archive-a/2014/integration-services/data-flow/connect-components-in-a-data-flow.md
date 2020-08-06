---
title: 데이터 흐름의 구성 요소 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc4a2fa81e9b110c27ea63b16d835d069bf12cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728575"
---
# <a name="connect-components-in-a-data-flow"></a><span data-ttu-id="905af-102">데이터 흐름의 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="905af-102">Connect Components in a Data Flow</span></span>
  <span data-ttu-id="905af-103">이 절차에서는 데이터 흐름의 구성 요소 출력을 동일 데이터 흐름 내의 다른 구성 요소에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="905af-103">This procedure describes how to connect the output of components in a data flow to other components within the same data flow.</span></span>  
  
### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="905af-104">데이터 흐름에서 구성 요소를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="905af-104">To connect components in a data flow</span></span>  
  
1.  <span data-ttu-id="905af-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="905af-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="905af-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="905af-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="905af-107">**제어 흐름** 탭을 클릭한 후 구성 요소를 연결하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="905af-107">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow in which you want to connect components.</span></span>  
  
4.  <span data-ttu-id="905af-108">**데이터 흐름** 탭의 디자인 화면에서 연결하려는 변환 또는 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="905af-108">On the design surface of the **Data Flow** tab, select the transformation or source that you want to connect.</span></span>  
  
5.  <span data-ttu-id="905af-109">변환 또는 원본의 녹색 출력 화살표를 변환 또는 대상으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="905af-109">Drag the green output arrow of a transformation or a source to a transformation or to a destination.</span></span> <span data-ttu-id="905af-110">일부 데이터 흐름 구성 요소에는 오류 출력이 포함되어 있으며 이 출력도 동일한 방법으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905af-110">Some data flow components have error outputs that you can connect in the same way.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="905af-111">일부 데이터 흐름 구성 요소에는 여러 출력이 포함될 수 있으며 각 출력을 서로 다른 변환이나 대상으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905af-111">Some data flow components can have multiple outputs and you can connect each output to a different transformation or destination.</span></span>  
  
6.  <span data-ttu-id="905af-112">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="905af-112">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905af-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="905af-113">See Also</span></span>  
 <span data-ttu-id="905af-114">[데이터 흐름에서 구성 요소 추가 또는 삭제](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="905af-114">[Add or Delete a Component in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="905af-115">[데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="905af-115">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="905af-116">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="905af-116">Data Flow</span></span>](data-flow.md)  
  
  
