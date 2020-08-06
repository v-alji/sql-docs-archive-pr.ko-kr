---
title: 인스턴스 이름 바꾸기 대화 상자 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.ssas.instancerename.f1
ms.assetid: 3708d992-8dd9-461c-8aa0-5da6df96ed70
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69d30a75f07197abce7990f6c55299a6064969db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659660"
---
# <a name="rename-instance-dialog-box-analysis-services"></a><span data-ttu-id="4de73-102">인스턴스 이름 바꾸기 대화 상자(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4de73-102">Rename Instance Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="4de73-103">**인스턴스 이름 바꾸기** 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 기존 인스턴스 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-103">Use the **Rename Instance** dialog box to rename an existing instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4de73-104">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE에서 **인스턴스 이름 바꾸기** 도구(asinstancerename.exe)를 실행하면 **인스턴스 이름 바꾸기** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-104">You can display the **Rename Instance** dialog box by launching the **Instance Rename** tool (asinstancerename.exe) from C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4de73-105">옵션</span><span class="sxs-lookup"><span data-stu-id="4de73-105">Options</span></span>  
  
|<span data-ttu-id="4de73-106">용어</span><span class="sxs-lookup"><span data-stu-id="4de73-106">Term</span></span>|<span data-ttu-id="4de73-107">정의</span><span class="sxs-lookup"><span data-stu-id="4de73-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="4de73-108">**이름을 바꿀 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="4de73-108">**Instance to rename**</span></span>|<span data-ttu-id="4de73-109">이름을 바꿀 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-109">Select the instance to be renamed.</span></span>|  
|<span data-ttu-id="4de73-110">**새 인스턴스 이름**</span><span class="sxs-lookup"><span data-stu-id="4de73-110">**New instance name**</span></span>|<span data-ttu-id="4de73-111">원하는 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-111">Type the desired instance name.</span></span> <span data-ttu-id="4de73-112">서버 이름은 포함하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="4de73-112">Do not include the server name.</span></span> <span data-ttu-id="4de73-113">즉, \<server name> \\<인스턴스 이름을 입력 하는 대신 \> 만 입력 \<instance name> 합니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-113">That is, instead of entering \<server name>\\<instance name\>, enter only \<instance name>.</span></span><br /><br /> <span data-ttu-id="4de73-114">이름을 바꾸려는 인스턴스가 기본 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스가 되도록 하려면 이름을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-114">If you want the instance you are renaming to be the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, leave the name blank.</span></span>|  
|<span data-ttu-id="4de73-115">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="4de73-115">**Username**</span></span>|<span data-ttu-id="4de73-116">서비스에서 시작하는 데 사용할 계정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-116">Shows the account the service will use to start.</span></span> <span data-ttu-id="4de73-117">사용자 이름은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-117">The user name cannot be changed.</span></span>|  
|<span data-ttu-id="4de73-118">**암호**</span><span class="sxs-lookup"><span data-stu-id="4de73-118">**Password**</span></span>|<span data-ttu-id="4de73-119">서비스 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4de73-119">Type the password of the service account.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4de73-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4de73-120">See Also</span></span>  
 [<span data-ttu-id="4de73-121">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="4de73-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
