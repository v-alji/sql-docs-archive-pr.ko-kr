---
title: 보안 컨텍스트 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.securitycontext.f1
ms.assetid: 238a4a4b-84bd-4b3d-9f02-f3adf57fa3af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58d5f71172ac16087ecc342342e70ade234226a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647902"
---
# <a name="security-context-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="42239-102">보안 컨텍스트 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="42239-102">Security Context Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="42239-103">**의** 보안 컨텍스트 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 대한 데이터 또는 메타데이터를 검사하는 데 사용되는 사용자 및 역할을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42239-103">Use the **Security Context** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to change the user and role used to examine data or metadata for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="42239-104">큐브 디자이너의 **계산** 탭 또는 **브라우저** 탭에서 **도구 모음** 창의 **보안 컨텍스트** 를 클릭하여 **보안 컨텍스트** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42239-104">You can display the **Security Context** dialog box by clicking **Security Context** in the **Toolbar** pane on either the **Calculations** tab or the **Browser** tab in Cube Designer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42239-105">옵션</span><span class="sxs-lookup"><span data-stu-id="42239-105">Options</span></span>  
 <span data-ttu-id="42239-106">**현재 사용자**</span><span class="sxs-lookup"><span data-stu-id="42239-106">**Current user**</span></span>  
 <span data-ttu-id="42239-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 데이터 및 메타데이터를 보는 동안 현재 사용자의 도메인과 사용자 이름을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42239-107">Select to use the domain and user name of the current user while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="42239-108">**다른 사용자**</span><span class="sxs-lookup"><span data-stu-id="42239-108">**Other user**</span></span>  
 <span data-ttu-id="42239-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 데이터 및 메타데이터를 보는 동안 사용할 다른 사용자 또는 그룹의 도메인과 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42239-109">Type the domain and user name of another user or group to use while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="42239-110">사용자 또는 그룹의 도메인과 이름은</span><span class="sxs-lookup"><span data-stu-id="42239-110">The domain and name of the user or group uses the following format:</span></span>  
  
 <span data-ttu-id="42239-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="42239-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="42239-112">**역할**</span><span class="sxs-lookup"><span data-stu-id="42239-112">**Roles**</span></span>  
 <span data-ttu-id="42239-113">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 데이터 및 메타데이터를 보는 동안 지정한 역할을 하나 이상 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42239-113">Select to use one or more specified roles when viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="42239-114">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 여러 개의 역할이 정의되어 있으면 사용할 역할을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42239-114">You can select the roles to use if multiple roles are defined in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42239-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42239-115">See Also</span></span>  
 <span data-ttu-id="42239-116">[큐브 디자이너 &#40;Kpi&#41; &#40;Analysis Services-다차원 데이터&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="42239-116">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="42239-117">[브라우저 &#40;큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="42239-117">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="42239-118">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="42239-118">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
