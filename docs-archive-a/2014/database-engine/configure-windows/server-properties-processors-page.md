---
title: 서버 속성(프로세서 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.processor.f1
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4d241f01de7ac961832e77bb09483cff275deb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651883"
---
# <a name="server-properties-processors-page"></a><span data-ttu-id="769eb-102">서버 속성(프로세서 페이지)</span><span class="sxs-lookup"><span data-stu-id="769eb-102">Server Properties (Processors Page)</span></span>
  <span data-ttu-id="769eb-103">이 페이지를 사용하여 프로세서 옵션을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-103">Use this page to view or modify your processor options.</span></span> <span data-ttu-id="769eb-104">프로세서 선호도 설정은 프로세서가 두 개 이상 설치되어 있는 경우에만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-104">Processor affinity settings are only enabled when more than one processor is installed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="769eb-105">옵션</span><span class="sxs-lookup"><span data-stu-id="769eb-105">Options</span></span>  
 <span data-ttu-id="769eb-106">**프로세서 선호도**</span><span class="sxs-lookup"><span data-stu-id="769eb-106">**Processor Affinity**</span></span>  
 <span data-ttu-id="769eb-107">특정 스레드에 프로세서를 할당하여 프로세서를 다시 로드해야 하는 필요성을 없애고 프로세스 간의 스레드 마이그레이션을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-107">Assigns processors to specific threads to eliminating processor reloads and reduce thread migration across processors.</span></span> <span data-ttu-id="769eb-108">자세한 내용은 [affinity mask 서버 구성 옵션](affinity-mask-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="769eb-108">For more information, see [affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="769eb-109">**I/O 선호도**</span><span class="sxs-lookup"><span data-stu-id="769eb-109">**I/O Affinity**</span></span>  
 <span data-ttu-id="769eb-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 디스크 I/O를 지정된 CPU 하위 집합에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-110">Binds [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/Os to a specified subset of CPUs.</span></span> <span data-ttu-id="769eb-111">자세한 내용은 [affinity Input-Output mask 서버 구성 옵션](affinity-input-output-mask-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="769eb-111">For more information, see [affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="769eb-112">**모든 프로세서에 대해 자동으로 프로세서 선호도 마스크 설정**</span><span class="sxs-lookup"><span data-stu-id="769eb-112">**Automatically set processor affinity mask for all processors**</span></span>  
 <span data-ttu-id="769eb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 프로세서 선호도를 자동으로 설정하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-113">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the processor affinity.</span></span>  
  
 <span data-ttu-id="769eb-114">**모든 프로세서에 대해 자동으로 I/O 선호도 마스크 설정**</span><span class="sxs-lookup"><span data-stu-id="769eb-114">**Automatically set I/O affinity mask for all processors**</span></span>  
 <span data-ttu-id="769eb-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 I/O 선호도를 자동으로 설정하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-115">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the I/O affinity.</span></span>  
  
 <span data-ttu-id="769eb-116">**최대 작업자 스레드 수**</span><span class="sxs-lookup"><span data-stu-id="769eb-116">**Maximum worker threads**</span></span>  
 <span data-ttu-id="769eb-117">0으로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 작업자 스레드 수를 동적으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-117">0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to dynamically set the number of worker threads.</span></span> <span data-ttu-id="769eb-118">이 설정은 대부분의 시스템에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-118">This setting is best for most systems.</span></span> <span data-ttu-id="769eb-119">그러나 시스템 구성에 따라 이 옵션을 특정 값으로 설정하면 성능이 향상되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-119">However, depending on your system configuration, setting this option to a specific value sometimes improves performance.</span></span> <span data-ttu-id="769eb-120">자세한 내용은 [Configure the max worker threads Server Configuration Option](configure-the-max-worker-threads-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="769eb-120">For more information, see [Configure the max worker threads Server Configuration Option](configure-the-max-worker-threads-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="769eb-121">**SQL Server 우선 순위 높임**</span><span class="sxs-lookup"><span data-stu-id="769eb-121">**Boost SQL Server priority**</span></span>  
 <span data-ttu-id="769eb-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 일정 예약 우선 순위를 같은 컴퓨터의 다른 프로세스보다 높여서 실행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-122">Specifies whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="769eb-123">자세한 내용은 [Configure the priority boost Server Configuration Option](configure-the-priority-boost-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="769eb-123">For more information, see [Configure the priority boost Server Configuration Option](configure-the-priority-boost-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="769eb-124">**Windows 파이버(경량 풀링) 사용**</span><span class="sxs-lookup"><span data-stu-id="769eb-124">**Use Windows fibers (lightweight pooling)**</span></span>  
 <span data-ttu-id="769eb-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 스레드 대신 Windows 파이버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-125">Use Windows fibers instead of threads for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="769eb-126">이 옵션은 Windows 2003 Server Edition에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-126">Note that this is only available in Windows 2003 Server Edition.</span></span> <span data-ttu-id="769eb-127">자세한 내용은 [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="769eb-127">For more information, see [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="769eb-128">**구성 값**</span><span class="sxs-lookup"><span data-stu-id="769eb-128">**Configured Values**</span></span>  
 <span data-ttu-id="769eb-129">이 창의 옵션에 대해 구성된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="769eb-130">이러한 값을 변경한 후에는 **실행 값** 을 클릭하여 변경 사항이 적용되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="769eb-131">변경 사항이 적용되지 않은 경우 먼저 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="769eb-132">**실행 값**</span><span class="sxs-lookup"><span data-stu-id="769eb-132">**Running Values**</span></span>  
 <span data-ttu-id="769eb-133">이 창의 옵션에 대한 현재 실행 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-133">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="769eb-134">이 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="769eb-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769eb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="769eb-135">See Also</span></span>  
 [<span data-ttu-id="769eb-136">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="769eb-136">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
