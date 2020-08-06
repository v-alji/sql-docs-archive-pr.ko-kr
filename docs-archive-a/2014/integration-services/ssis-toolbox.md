---
title: SSIS 도구 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.toolboxcommon.F1
- sql12.dts.designer.toolbox.F1
- sql12.dts.designer.toolboxfavorites.F1
ms.assetid: 552ff592-eeef-46e8-b4a2-9b2384c869aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed35218c84c77d3116ab8c897fe51fab5d6359aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734315"
---
# <a name="ssis-toolbox"></a><span data-ttu-id="63fed-102">SSIS 도구 상자</span><span class="sxs-lookup"><span data-stu-id="63fed-102">SSIS Toolbox</span></span>
  <span data-ttu-id="63fed-103">SQL Server 2008 및 2008 R2용으로 작성된 타사 구성 요소를 포함하여 로컬 컴퓨터에 설치되는 모든 구성 요소는 이제 새 **SSIS 도구 상자**에 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-103">All components that are installed on the local machine, including third-party components built for SQL Server 2008 and 2008 R2, now automatically appear in the new **SSIS Toolbox**.</span></span> <span data-ttu-id="63fed-104">추가 구성 요소를 설치할 때는 도구 상자 내부를 마우스 오른쪽 단추로 클릭한 다음 **도구 상자 새로 고침** 을 클릭하여 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-104">When you install additional components, right-click inside the toolbox and then click **Refresh Toolbox** to add the components.</span></span>  
  
 <span data-ttu-id="63fed-105">구성 요소를 클릭하여 도구 상자 아래쪽의 설명을 보면 도구 상자에서 구성 요소에 대한 자세한 내용에 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-105">You can easily access more information about a component from the toolbox, by clicking the component to view a description at the bottom of the toolbox.</span></span> <span data-ttu-id="63fed-106">설명 옆의 도움말 단추를 클릭하여 온라인 설명서 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-106">Click the Help button next to the description to display the Books Online topic.</span></span> <span data-ttu-id="63fed-107">일부 구성 요소의 경우 해당 구성 요소를 구성하고 사용하는 방법을 보여 주는 예제에도 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-107">For certain components, you can also access samples that demonstrate how to configure and use the components.</span></span> <span data-ttu-id="63fed-108">예제는 [MSDN](https://go.microsoft.com/fwlink/?LinkId=259189)에서 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-108">The samples are available on [MSDN](https://go.microsoft.com/fwlink/?LinkId=259189).</span></span> <span data-ttu-id="63fed-109">**SSIS 도구 상자**에서 예제에 액세스하려면 설명 아래에 표시되는 **샘플 찾기** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-109">To access the samples from the **SSIS Toolbox**, click the **Find Samples** link that appears below the description.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63fed-110">이전 버전의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]와 달리 설치된 구성 요소를 도구 상자에서 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-110">Unlike previous versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you cannot remove installed components from the toolbox.</span></span>  
  
 <span data-ttu-id="63fed-111">**SSIS 도구 상자**에서 제어 흐름 및 데이터 흐름 구성 요소는 범주로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-111">In the **SSIS Toolbox**, control flow and data flow components are organized into categories.</span></span>  <span data-ttu-id="63fed-112">범주를 확장하고 축소해서 볼 수 있으며 기본 설정에 따라 구성 요소의 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-112">You can expand and collapse categories for viewing and you can change the organization of components according to your preferences.</span></span>  <span data-ttu-id="63fed-113">도구 상자 내부를 마우스 오른쪽 단추로 클릭한 다음 **도구 상자 기본값 복원**을 클릭하여 기본 구성을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-113">You can restore the default organization, by right-clicking inside the toolbox and then click **Restore Toolbox Defaults**.</span></span>  
  
 <span data-ttu-id="63fed-114">**제어 흐름** , **데이터 흐름** 및 **이벤트 처리기**탭을 선택하면 **즐겨찾기**및 **공용** 범주가 도구 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-114">The **Favorites** and **Common** categories appear in the toolbox when you select the **Control Flow**, **Data Flow**, and **Event Handlers** tabs.</span></span> <span data-ttu-id="63fed-115">**제어 흐름** 탭 또는 **이벤트 처리기** 탭을 선택 하면 **다른 작업** 범주가 도구 상자에 나타납니다. **데이터 흐름** 탭을 선택 하면 **기타 변환**, **기타 원본**및 **기타 대상** 범주가 도구 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-115">The **Other Tasks** category appears in the toolbox when you select the **Control Flow** tab or the **Event Handlers** tab. The **Other Transforms**, **Other Sources**, and **Other Destinations** categories appear in the toolbox when you select the **Data Flow** tab.</span></span>  
  
 <span data-ttu-id="63fed-116">새 SSIS 프로젝트를 만들거나 기존 프로젝트를 열면 **SSIS 도구 상자** 가 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-116">When you create a new SSIS project or open an existing project, the **SSIS Toolbox** is automatically displayed.</span></span> <span data-ttu-id="63fed-117">패키지 디자인 화면의 오른쪽 위에 있는 도구 상자 단추를 클릭하여 도구 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-117">You can also open the toolbox by clicking the toolbox button that is located in the top-right corner of the package design surface.</span></span>  
  
 <span data-ttu-id="63fed-118">도구 상자를 도킹하고 도킹할 때 축소하도록 설정할 수 있으며 도구 상자를 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fed-118">You can dock the toolbox, set it to collapse when docked, and you can close the toolbox.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="63fed-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="63fed-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="63fed-120">SSIS 도구 상자 항목 이동</span><span class="sxs-lookup"><span data-stu-id="63fed-120">Move SSIS Toolbox Items</span></span>](../../2014/integration-services/move-ssis-toolbox-items.md)  
  
  
