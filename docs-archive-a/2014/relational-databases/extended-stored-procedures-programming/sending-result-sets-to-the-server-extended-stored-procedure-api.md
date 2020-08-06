---
title: 서버에 결과 집합 보내기 (확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638782"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a><span data-ttu-id="97a3e-102">서버로 결과 집합 보내기(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="97a3e-102">Sending Result Sets to the Server (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="97a3e-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="97a3e-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="97a3e-104">로 결과 집합을 보낼 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 저장 프로시저는 다음과 같이 적절 한 API를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-104">When sending a result set to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the extended stored procedure should call the appropriate API as follows:</span></span>  
  
-   <span data-ttu-id="97a3e-105">**Srv_sendmsg** 함수는 **srv_sendrow**를 사용 하 여 모든 행 (있는 경우)이 전송 되기 전이나 후에 순서에 관계 없이 호출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-105">The **srv_sendmsg** function may be called in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="97a3e-106">**Srv_senddone**를 사용 하 여 완료 상태를 보내기 전에 모든 메시지를 클라이언트로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-106">All messages must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="97a3e-107">클라이언트로 보내는 각 행에 대해 한 번씩 **srv_sendrow** 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-107">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="97a3e-108">메시지, 상태 값 또는 완료 상태가 **srv_sendmsg**, **srv_pfield**의 **srv_status** 인수 또는 **srv_senddone**를 전송 하기 전에 모든 행을 클라이언트로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-108">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, the **srv_status** argument of **srv_pfield**, or **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="97a3e-109">**Srv_describe** 를 사용 하 여 정의 된 모든 열이 없는 행을 보내면 응용 프로그램에서 정보 오류 메시지를 발생 시키고 클라이언트에 FAIL을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-109">Sending a row that has not had all its columns defined with **srv_describe** causes the application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="97a3e-110">이 경우 행이 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97a3e-110">In this case, the row is not sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a3e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97a3e-111">See Also</span></span>  
 [<span data-ttu-id="97a3e-112">확장 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="97a3e-112">Creating Extended Stored Procedures</span></span>](creating-extended-stored-procedures.md)  
  
  
