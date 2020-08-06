---
title: c2 audit mode 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3407a2a94a43adb2d3d3b52994093d6ed0c2e684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740437"
---
# <a name="c2-audit-mode-server-configuration-option"></a><span data-ttu-id="17eb2-102">c2 audit mode 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="17eb2-102">c2 audit mode Server Configuration Option</span></span>
  <span data-ttu-id="17eb2-103">C2 Audit Mode는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 통해 구성하거나 **sp_configure** 에 **c2 audit mode**옵션을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-103">C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or with the **c2 audit mode** option in **sp_configure**.</span></span> <span data-ttu-id="17eb2-104">이 옵션을 선택하면 문과 개체에 대해 실패한 액세스 시도와 성공한 액세스 시도를 모두 기록하도록 서버가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-104">Selecting this option will configure the server to record both failed and successful attempts to access statements and objects.</span></span> <span data-ttu-id="17eb2-105">이 정보는 시스템 동작을 파악하고 보안 정책 위반을 추적하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-105">This information can help you profile system activity and track possible security policy violations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="17eb2-106">C2 보안 표준은 Common Criteria 인증으로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-106">The C2 security standard has been superseded by Common Criteria Certification.</span></span> <span data-ttu-id="17eb2-107">[common criteria compliance enabled 서버 구성 옵션](common-criteria-compliance-enabled-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17eb2-107">See the [common criteria compliance enabled Server Configuration Option](common-criteria-compliance-enabled-server-configuration-option.md).</span></span>  
  
## <a name="audit-log-file"></a><span data-ttu-id="17eb2-108">감사 로그 파일</span><span class="sxs-lookup"><span data-stu-id="17eb2-108">Audit Log File</span></span>  
 <span data-ttu-id="17eb2-109">C2 Audit Mode 데이터는 인스턴스의 기본 데이터 디렉터리에 파일로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-109">C2 audit mode data is saved in a file in the default data directory of the instance.</span></span> <span data-ttu-id="17eb2-110">감사 로그 파일 크기가 제한 크기(200MB)에 도달하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 새 파일을 만들고 기존 파일을 닫은 후 새로운 감사 기록을 모두 새 파일에 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-110">If the audit log file reaches its size limit of 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will create a new file, close the old file, and write all new audit records to the new file.</span></span> <span data-ttu-id="17eb2-111">이러한 프로세스는 감사 데이터 디렉터리가 꽉 차거나 감사 옵션이 해제될 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-111">This process will continue until the audit data directory fills up or auditing is turned off.</span></span> <span data-ttu-id="17eb2-112">C2 추적의 상태를 확인하려면 sys.traces 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-112">To determine the status of a C2 trace, query the sys.traces catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17eb2-113">C2 Audit Mode를 사용하면 로그 파일에 많은 양의 이벤트 정보가 저장되어 파일의 크기가 빠르게 커집니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-113">C2 audit mode saves a large amount of event information to the log file, which can grow quickly.</span></span> <span data-ttu-id="17eb2-114">로그 파일이 저장되는 데이터 디렉터리의 공간이 부족하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 자동으로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-114">If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will shut itself down.</span></span> <span data-ttu-id="17eb2-115">감사가 자동으로 시작되도록 설정되어 있으면 감사 프로세스를 생략하도록 하는 **-f** 플래그를 사용하여 인스턴스를 다시 시작하거나 감사 로그를 저장할 수 있는 디스크 공간을 추가로 확보해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-115">If auditing is set to start automatically, you must either restart the instance with the **-f** flag (which bypasses auditing), or free up additional disk space for the audit log.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="17eb2-116">사용 권한</span><span class="sxs-lookup"><span data-stu-id="17eb2-116">Permissions</span></span>  
 <span data-ttu-id="17eb2-117">**sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-117">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17eb2-118">예제</span><span class="sxs-lookup"><span data-stu-id="17eb2-118">Example</span></span>  
 <span data-ttu-id="17eb2-119">다음 예에서는 C2 Audit Mode를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17eb2-119">The following example turns on C2 audit mode.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="17eb2-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17eb2-120">See Also</span></span>  
 <span data-ttu-id="17eb2-121">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17eb2-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="17eb2-122">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="17eb2-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="17eb2-123">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17eb2-123">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
