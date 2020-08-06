---
title: 복제 모니터 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cff23206923825d0e86e47ad6921c19f45e68b35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741827"
---
# <a name="start-the-replication-monitor"></a><span data-ttu-id="c1080-102">복제 모니터 시작</span><span class="sxs-lookup"><span data-stu-id="c1080-102">Start the Replication Monitor</span></span>
  <span data-ttu-id="c1080-103">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 의 인스턴스에 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]나 명령 프롬프트에서 복제 모니터를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-103">Replication Monitor can be started from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or from the command prompt.</span></span> <span data-ttu-id="c1080-104">복제 모니터를 시작한 후 모니터링할 하나 이상의 게시자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-104">After starting Replication Monitor, add one or more Publishers to monitor.</span></span> <span data-ttu-id="c1080-105">자세한 내용은 [복제 모니터에서 게시자 추가 및 제거](add-and-remove-publishers-from-replication-monitor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1080-105">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a><span data-ttu-id="c1080-106">SQL Server Management Studio에서 복제 모니터를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="c1080-106">To start Replication Monitor from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="c1080-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]인스턴스에 연결한 다음 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-107">Connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="c1080-108">**복제** 폴더 또는 하위 폴더를 마우스 오른쪽 단추로 클릭한 다음 **복제 모니터 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-108">Right-click the **Replication** folder or any of its subfolders, and then click **Launch Replication Monitor**.</span></span>  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a><span data-ttu-id="c1080-109">명령 프롬프트에서 복제 모니터를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="c1080-109">To start Replication Monitor from the command prompt</span></span>  
  
1.  <span data-ttu-id="c1080-110">명령 프롬프트에서 도구 설치 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-110">From the command prompt, navigate to the tools installation directory.</span></span> <span data-ttu-id="c1080-111">기본 경로는 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\입니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-111">The default path is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ .</span></span>  
  
2.  <span data-ttu-id="c1080-112">sqlmonitor.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1080-112">Run sqlmonitor.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1080-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1080-113">See Also</span></span>  
 [<span data-ttu-id="c1080-114">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="c1080-114">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
