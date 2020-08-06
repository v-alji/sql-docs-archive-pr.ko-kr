---
title: 확장 저장 프로시저의 작동 방식 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653390"
---
# <a name="how-extended-stored-procedures-work"></a><span data-ttu-id="9b3d4-102">확장 저장 프로시저 작동 원리</span><span class="sxs-lookup"><span data-stu-id="9b3d4-102">How Extended Stored Procedures Work</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="9b3d4-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b3d4-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="9b3d4-104">확장 저장 프로시저가 작동하는 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b3d4-104">The process by which an extended stored procedure works is:</span></span>  
  
1.  <span data-ttu-id="9b3d4-105">클라이언트에서 확장 저장 프로시저를 실행 하면 요청이 TDS (tabular data stream) 또는 SOAP (Simple Object Access Protocol) 형식으로 클라이언트 응용 프로그램에서로 전송 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9b3d4-105">When a client executes an extended stored procedure, the request is transmitted in tabular data stream (TDS) or Simple Object Access Protocol (SOAP) format from the client application to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9b3d4-106">가 확장 저장 프로시저와 연결된 DLL을 검색하고 아직 로드되지 않은 경우 DLL을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9b3d4-106">searches for the DLL associated with the extended stored procedure, and loads the DLL if it is not already loaded.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9b3d4-107">가 요청된 확장 저장 프로시저(DLL 내에 함수로 구현됨)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9b3d4-107">calls the requested extended stored procedure (implemented as a function inside the DLL).</span></span>  
  
4.  <span data-ttu-id="9b3d4-108">확장 저장 프로시저가 결과 집합을 전달하고 확장 저장 프로시저 API를 통해 매개 변수를 서버로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9b3d4-108">The extended stored procedure passes result sets and return parameters back to the server by through the Extended Stored Procedure API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3d4-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b3d4-109">See Also</span></span>  
 [<span data-ttu-id="9b3d4-110">데이터베이스 엔진 확장 저장 프로시저 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="9b3d4-110">Database Engine Extended Stored Procedure Programming</span></span>](../database-engine-extended-stored-procedure-programming.md)  
  
  
