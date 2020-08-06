---
title: 서버 속성(기타 서버 설정 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a82a787140141c3bfa7b18776328a813be9f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651892"
---
# <a name="server-properties-misc-server-settings-page"></a><span data-ttu-id="2a44a-102">서버 속성(기타 서버 설정 페이지)</span><span class="sxs-lookup"><span data-stu-id="2a44a-102">Server Properties (Misc Server Settings Page)</span></span>
  <span data-ttu-id="2a44a-103">이 페이지를 사용하여 서버 설정을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-103">Use this page to view or modify your server settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a44a-104">옵션</span><span class="sxs-lookup"><span data-stu-id="2a44a-104">Options</span></span>  
 <span data-ttu-id="2a44a-105">**사용자의 기본 언어**</span><span class="sxs-lookup"><span data-stu-id="2a44a-105">**Default language for users**</span></span>  
 <span data-ttu-id="2a44a-106">새로 생성된 모든 로그인에 대한 기본 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-106">Specifies the default language for all newly created logins.</span></span>  
  
 <span data-ttu-id="2a44a-107">**다른 트리거를 발생시키는 트리거 허용**</span><span class="sxs-lookup"><span data-stu-id="2a44a-107">**Allow triggers to fire other triggers**</span></span>  
 <span data-ttu-id="2a44a-108">트리거로 다른 트리거를 시작할 수 있는지 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-108">Controls whether a trigger can perform an action that initiates another trigger.</span></span> <span data-ttu-id="2a44a-109">이 옵션의 선택을 취소하면 트리거로 다른 트리거를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-109">When cleared, triggers cannot be fired by another trigger.</span></span> <span data-ttu-id="2a44a-110">이 옵션을 선택하면 최대 32 수준까지 트리거에 의한 트리거 시작이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-110">When selected, triggers can be fired by other triggers to as many as 32 levels.</span></span>  
  
 <span data-ttu-id="2a44a-111">**쿼리 관리자를 사용하여 장기 실행 쿼리 방지**</span><span class="sxs-lookup"><span data-stu-id="2a44a-111">**Use query governor to prevent long-running queries**</span></span>  
 <span data-ttu-id="2a44a-112">쿼리가 실행될 수 있는 최대 제한 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-112">Specifies an upper limit on the time within which a query can run.</span></span> <span data-ttu-id="2a44a-113">쿼리 비용이란 특정 하드웨어 구성에서 쿼리를 실행하는 데 필요한 예상 소요 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-113">Query cost refers to the estimated elapsed time, in seconds, required to execute a query on a specific hardware configuration.</span></span> <span data-ttu-id="2a44a-114">기본적으로 쿼리 관리자는 해제되어 있어 모든 쿼리의 실행이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-114">By default, the query governor is turned off and all queries are allowed to run.</span></span> <span data-ttu-id="2a44a-115">이 옵션을 선택하면 아래의 입력란에 제한 시간을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-115">If this option is selected, you must enter a time limit in the text box below.</span></span> <span data-ttu-id="2a44a-116">0이나 음수가 아닌 값을 지정하면 쿼리 관리자가 그 값을 초과하는 예상 비용을 갖는 쿼리의 실행을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-116">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost exceeding that value.</span></span>  
  
 <span data-ttu-id="2a44a-117">**두 자리 연도를 다음 연도로 해석**</span><span class="sxs-lookup"><span data-stu-id="2a44a-117">**Interpret a two-digit year as falling between**</span></span>  
 <span data-ttu-id="2a44a-118">두 자리 연도 값 해석에 사용할 100년 간의 날짜 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-118">Specifies the 100-year date range for interpreting two-digit year values.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2a44a-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 지정된 범위 내에서 마지막 두 자리가 일치하는 연도를 참조하여 두 자리 날짜 값을 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will interpret two-digit date values to refer to the year ending in those digits that falls within the specified range.</span></span>  
  
 <span data-ttu-id="2a44a-120">오른쪽 상자에서 끝 연도를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-120">Set the right box with the ending year.</span></span> <span data-ttu-id="2a44a-121">끝 연도를 저장하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 은 자동으로 왼쪽 상자에 시작 연도를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-121">When the ending year is saved, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will automatically populate the left box with the beginning year.</span></span>  
  
 <span data-ttu-id="2a44a-122">**구성 값**</span><span class="sxs-lookup"><span data-stu-id="2a44a-122">**Configured Values**</span></span>  
 <span data-ttu-id="2a44a-123">이 창의 옵션에 대해 구성된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-123">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="2a44a-124">이러한 값을 변경한 후에는 **실행 값** 을 클릭하여 변경 사항이 적용되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-124">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="2a44a-125">변경 사항이 적용되지 않은 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-125">If the changes have not taken effect, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="2a44a-126">**실행 값**</span><span class="sxs-lookup"><span data-stu-id="2a44a-126">**Running Values**</span></span>  
 <span data-ttu-id="2a44a-127">이 창의 옵션에 대한 현재 실행 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-127">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="2a44a-128">이 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-128">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a44a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a44a-129">See Also</span></span>  
 [<span data-ttu-id="2a44a-130">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a44a-130">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
