---
title: 데이터 흐름 경로 편집기를 사용 하 여 경로의 속성 설정 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 512249a4-83a6-4087-980d-a4344da48371
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e01565ef6cb70f3ac52187a6cc8d22d05508db4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742387"
---
# <a name="set-the-properties-of-a-path-by-using-the-data-flow-path-editor"></a><span data-ttu-id="5bf2e-102">데이터 흐름 경로 편집기를 사용하여 경로의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="5bf2e-102">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>
  <span data-ttu-id="5bf2e-103">경로는 두 개의 데이터 흐름 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-103">Paths connect two data flow components.</span></span> <span data-ttu-id="5bf2e-104">경로 메타데이터를 설정하려면 데이터 흐름에 적어도 두 개 이상의 연결된 데이터 흐름 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-104">Before you can set path properties, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="5bf2e-105">자세한 내용은 [데이터 흐름에서 구성 요소 추가 또는 삭제](data-flow/add-or-delete-a-component-in-a-data-flow.md) 및 [데이터 흐름의 구성 요소 연결](data-flow/connect-components-in-a-data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-set-path-properties"></a><span data-ttu-id="5bf2e-106">경로 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="5bf2e-106">To set path properties</span></span>  
  
1.  <span data-ttu-id="5bf2e-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="5bf2e-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="5bf2e-109">**데이터 흐름** 탭을 클릭한 후 경로를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-109">Click the **Data Flow** tab, and then double-click a path.</span></span>  
  
4.  <span data-ttu-id="5bf2e-110">**데이터 흐름 경로 편집기**에서 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-110">In **Data Flow Path Editor**, click **General**.</span></span> <span data-ttu-id="5bf2e-111">그러면 경로의 기본 이름을 편집하고 경로에 대한 설명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-111">You can then edit the default name of the path and provide a description of the path.</span></span> <span data-ttu-id="5bf2e-112">또한 PathAnnotation 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-112">You can also modify the PathAnnotation property.</span></span>  
  
5.  <span data-ttu-id="5bf2e-113">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-113">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="5bf2e-114">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf2e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bf2e-115">See Also</span></span>  
 <span data-ttu-id="5bf2e-116">[Integration Services 경로](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="5bf2e-116">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="5bf2e-117">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="5bf2e-117">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
