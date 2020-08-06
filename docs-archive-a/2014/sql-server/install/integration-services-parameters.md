---
title: Integration Services 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740727"
---
# <a name="integration-services-parameters"></a><span data-ttu-id="c82f7-102">Integration Services 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c82f7-102">Integration Services Parameters</span></span>
  <span data-ttu-id="c82f7-103">의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 컴퓨터의 패키지나 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 파일 시스템의 패키지 파일을 분석 하도록 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-103">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you can decide to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer, or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package files in the file system.</span></span> <span data-ttu-id="c82f7-104">파일 시스템에 있는 파일을 분석할 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 들어 있는 폴더의 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-104">If you analyze files in the file system, provide a path to the folder that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c82f7-105">옵션</span><span class="sxs-lookup"><span data-stu-id="c82f7-105">Options</span></span>  
 <span data-ttu-id="c82f7-106">**컴퓨터에 있는 SSIS 패키지 분석**</span><span class="sxs-lookup"><span data-stu-id="c82f7-106">**Analyze SSIS packages on Computer**</span></span>  
 <span data-ttu-id="c82f7-107">컴퓨터에 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 분석하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-107">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer.</span></span> <span data-ttu-id="c82f7-108">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-108">By default, this option is selected.</span></span>  
  
 <span data-ttu-id="c82f7-109">**SSIS 패키지 파일 분석**</span><span class="sxs-lookup"><span data-stu-id="c82f7-109">**Analyze SSIS package files**</span></span>  
 <span data-ttu-id="c82f7-110">파일 시스템에 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 분석하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-110">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages in the file system.</span></span>  
  
 <span data-ttu-id="c82f7-111">**SSIS 패키지의 경로**</span><span class="sxs-lookup"><span data-stu-id="c82f7-111">**Path to SSIS packages**</span></span>  
 <span data-ttu-id="c82f7-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 들어 있는 UNC 또는 로컬 경로를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-112">Locate a UNC or local path that holds your [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="c82f7-113">파일 이름을 포함할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-113">You do not have to include file names.</span></span> <span data-ttu-id="c82f7-114">입력 한 경로에 액세스할 수 없으면 **다음**을 클릭할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-114">If the path you have entered cannot be accessed, you cannot click **Next**.</span></span> <span data-ttu-id="c82f7-115">기본적으로 경로는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-115">By default, the path is blank.</span></span> <span data-ttu-id="c82f7-116">이 필드는 **SSIS 패키지 파일 분석**을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c82f7-116">This field is enabled only when you select **Analyze SSIS package files**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82f7-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c82f7-117">See Also</span></span>  
 <span data-ttu-id="c82f7-118">[업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="c82f7-118">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="c82f7-119">업그레이드 관리자 사용자 인터페이스 참조</span><span class="sxs-lookup"><span data-stu-id="c82f7-119">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
