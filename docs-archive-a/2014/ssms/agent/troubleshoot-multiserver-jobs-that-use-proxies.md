---
title: 프록시를 사용하는 다중 서버 작업 문제 해결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19de975ef5e1f22c93cec72a5014a01da5b03dd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731307"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a><span data-ttu-id="548a2-102">프록시를 사용하는 다중 서버 작업 문제 해결</span><span class="sxs-lookup"><span data-stu-id="548a2-102">Troubleshoot Multiserver Jobs That Use Proxies</span></span>
  <span data-ttu-id="548a2-103">프록시와 연관된 단계가 있는 분산된 작업은 대상 서버의 프록시 계정 컨텍스트 하에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="548a2-103">Distributed jobs whose steps are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="548a2-104">마스터 서버에서 다운로드할 때 프록시 계정을 사용하는 작업 단계가 실패한 경우 **msdb** 데이터베이스 **sysdownloadlist** 테이블의 **error_message** 열에서 다음 오류 메시지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="548a2-104">If job steps that use proxy accounts fail when downloaded from the master server, check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="548a2-105">"작업 단계에 프록시 계정이 필요하지만 일치하는 프록시를 대상 서버에서 사용할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="548a2-105">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="548a2-106">이 오류를 해결 하려면 **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.** 를 설정 하십시오. _ \<n_> **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** 레지스트리 하위 키를 **1 (true)로 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="548a2-106">To resolve this error, set the **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.**_\<n_>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** registry subkey to **1 (true)**.</span></span> <span data-ttu-id="548a2-107">기본적으로이 하위 키는 **0** ()으로 설정 됩니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="548a2-107">By default, this subkey is set to **0** (`false`).</span></span> <span data-ttu-id="548a2-108">MSSQL의 값입니다 **.**\<*n*></span><span class="sxs-lookup"><span data-stu-id="548a2-108">The value of **MSSQL.**\<*n*></span></span> <span data-ttu-id="548a2-109">는 인스턴스 이름입니다. 예를 들어 **mssql. 1** 또는 **mssql. 3**입니다.</span><span class="sxs-lookup"><span data-stu-id="548a2-109">is the instance name; for example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
-   <span data-ttu-id="548a2-110">"프록시를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="548a2-110">"Proxy not found."</span></span>  
  
     <span data-ttu-id="548a2-111">이 오류를 해결하려면 프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="548a2-111">To resolve this error, make sure a proxy account exists on the target server with the same name as the master server proxy account under which the job step runs.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="548a2-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="548a2-112">See Also</span></span>  
 [<span data-ttu-id="548a2-113">다중 서버 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="548a2-113">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
  
  
