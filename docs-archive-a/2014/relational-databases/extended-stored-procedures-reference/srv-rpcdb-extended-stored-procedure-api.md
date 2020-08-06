---
title: srv_rpcdb(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c951a4a821bbd49748182d9ddf5df017344a174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739988"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a><span data-ttu-id="179ac-102">srv_rpcdb(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="179ac-102">srv_rpcdb (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="179ac-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="179ac-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="179ac-104">현재 원격 저장 프로시저에 대한 데이터베이스 이름 구성 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-104">Returns the database name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179ac-105">구문</span><span class="sxs-lookup"><span data-stu-id="179ac-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="179ac-106">인수</span><span class="sxs-lookup"><span data-stu-id="179ac-106">Arguments</span></span>  
 <span data-ttu-id="179ac-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="179ac-107">*srvproc*</span></span>  
 <span data-ttu-id="179ac-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="179ac-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="179ac-110">*길이가*</span><span class="sxs-lookup"><span data-stu-id="179ac-110">*len*</span></span>  
 <span data-ttu-id="179ac-111">데이터베이스 이름의 길이를 받는 `int` 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-111">Is a pointer to an `int` variable that receives the length of the database name.</span></span> <span data-ttu-id="179ac-112">*len*이 NULL이면 데이터베이스 이름의 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-112">If *len* is NULL, the length of the database name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="179ac-113">반환</span><span class="sxs-lookup"><span data-stu-id="179ac-113">Returns</span></span>  
 <span data-ttu-id="179ac-114">현재 원격 저장 프로시저의 데이터베이스 이름 부분에서 null로 끝나는 문자열에 대한 DBCHAR 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-114">A DBCHAR pointer to the null-terminated string for the database name part of the current remote stored procedure.</span></span> <span data-ttu-id="179ac-115">현재 원격 저장 프로시저가 없으면 NULL이 반환되고 *len* 매개 변수가 -1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-115">If there is no current remote stored procedure, NULL is returned and the *len* parameter is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="179ac-116">설명</span><span class="sxs-lookup"><span data-stu-id="179ac-116">Remarks</span></span>  
 <span data-ttu-id="179ac-117">이 함수는 원격 저장 프로시저 개체 이름에서 데이터베이스 구성 요소만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-117">This function returns only the database component of the remote stored procedure object name.</span></span> <span data-ttu-id="179ac-118">소유자, 원격 저장 프로시저 이름, 원격 저장 프로시저 번호에 대한 선택적 지정자는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-118">It does not include the optional specifiers for owner, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="179ac-119">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="179ac-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="179ac-120">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="179ac-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
