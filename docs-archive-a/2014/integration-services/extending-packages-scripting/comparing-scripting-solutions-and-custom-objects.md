---
title: 스크립팅 솔루션과 사용자 지정 개체 비교 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: acf6faf9cdd78e951b8298c4e3b144d3444fb1ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647156"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a><span data-ttu-id="c5e51-102">스크립팅 솔루션과 사용자 지정 개체 비교</span><span class="sxs-lookup"><span data-stu-id="c5e51-102">Comparing Scripting Solutions and Custom Objects</span></span>
  <span data-ttu-id="c5e51-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 스크립트 태스크 또는 스크립트 구성 요소에서는 관리되는 사용자 지정 태스크 또는 데이터 흐름 구성 요소에서 사용할 수 있는 기능의 대부분을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task or Script component can implement much of the same functionality that is possible in a custom managed task or data flow component.</span></span> <span data-ttu-id="c5e51-104">다음은 개발자의 요구 사항에 적합한 태스크 유형을 선택할 때 고려할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-104">Here are some considerations to help you choose the appropriate type of task for your needs:</span></span>  
  
-   <span data-ttu-id="c5e51-105">구성 또는 기능이 개별 패키지에 고유한 경우 사용자 지정 개체를 개발하는 대신 스크립트 태스크나 스크립트 구성 요소를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-105">If the configuration or functionality is specific to an individual package, you should use the Script task or the Script component instead of a developing a custom object.</span></span>  
  
-   <span data-ttu-id="c5e51-106">기능이 일반적이고 나중에 다른 패키지에서 사용하거나 다른 개발자가 사용할 수도 있는 경우 스크립팅 솔루션을 사용하는 대신 사용자 지정 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-106">If the functionality is generic, and might be used in the future for other packages and by other developers, you should create a custom object instead of using a scripting solution.</span></span> <span data-ttu-id="c5e51-107">사용자 지정 개체는 모든 패키지에서 사용할 수 있는 반면 스크립트는 해당 스크립트가 만들어진 패키지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-107">You can use a custom object in any package, whereas a script can be used only in the package for which it was created.</span></span>  
  
-   <span data-ttu-id="c5e51-108">동일한 패키지 내에서 코드를 다시 사용하려는 경우 사용자 지정 개체를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-108">If the code will be reused within the same package, you should consider creating a custom object.</span></span> <span data-ttu-id="c5e51-109">스크립트 태스크나 구성 요소 간에 코드를 복사하면 코드의 여러 복사본을 관리 및 업데이트하기가 어려워지므로 유지 관리 성능이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-109">Copying code from one Script task or component to another leads to reduced maintainability by making it more difficult to maintain and update multiple copies of the code.</span></span>  
  
-   <span data-ttu-id="c5e51-110">시간이 경과하면서 구현이 변경될 경우 사용자 지정 개체를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-110">If the implementation will change over time, consider using a custom object.</span></span> <span data-ttu-id="c5e51-111">사용자 지정 개체는 부모 패키지와는 별도로 개발 및 배포할 수 있는 반면, 스크립팅 솔루션은 업데이트할 경우 패키지 전체를 다시 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5e51-111">Custom objects can be developed and deployed separately from the parent package, whereas an update made to a scripting solution requires the redeployment of the whole package.</span></span>  
  
<span data-ttu-id="c5e51-112">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c5e51-112">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c5e51-113">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c5e51-113">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c5e51-114">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c5e51-114">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c5e51-115">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="c5e51-115">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e51-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5e51-116">See Also</span></span>  
 [<span data-ttu-id="c5e51-117">사용자 지정 개체를 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="c5e51-117">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
