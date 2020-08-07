---
title: bcp_columns | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: rothja
ms.author: jroth
ms.openlocfilehash: 028bb80e88a29b366e3a489abae06c8b3b30cdf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730647"
---
# <a name="bcp_columns"></a><span data-ttu-id="330df-102">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="330df-102">bcp_columns</span></span>
  <span data-ttu-id="330df-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서의 대량 복사에 사용하기 위해 사용자 파일에서 찾는 총 열 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="330df-103">Sets the total number of columns found in the user file for use with a bulk copy into or out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="330df-104">bcp_columns 및 [bcp_colfmt](bcp-colfmt.md)대신 [bcp_setbulkmode](bcp-setbulkmode.md) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="330df-104">[bcp_setbulkmode](bcp-setbulkmode.md) can be used instead of bcp_columns and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330df-105">구문</span><span class="sxs-lookup"><span data-stu-id="330df-105">Syntax</span></span>  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="330df-106">인수</span><span class="sxs-lookup"><span data-stu-id="330df-106">Arguments</span></span>  
 <span data-ttu-id="330df-107">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="330df-107">*hdbc*</span></span>  
 <span data-ttu-id="330df-108">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="330df-108">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="330df-109">*nColumns*</span><span class="sxs-lookup"><span data-stu-id="330df-109">*nColumns*</span></span>  
 <span data-ttu-id="330df-110">사용자 파일에 포함된 총 열 수입니다.</span><span class="sxs-lookup"><span data-stu-id="330df-110">Is the total number of columns in the user file.</span></span> <span data-ttu-id="330df-111">사용자 파일에서 테이블로 데이터를 대량 복사 하 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고 사용자 파일의 모든 열을 복사 하지 않으려는 경우에도 *ncolumns* 를 총 사용자 파일 열 수로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="330df-111">Even if you are preparing to bulk copy data from the user file to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and do not intend to copy all columns in the user file, you must still set *nColumns* to the total number of user-file columns.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="330df-112">반환</span><span class="sxs-lookup"><span data-stu-id="330df-112">Returns</span></span>  
 <span data-ttu-id="330df-113">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="330df-113">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="330df-114">설명</span><span class="sxs-lookup"><span data-stu-id="330df-114">Remarks</span></span>  
 <span data-ttu-id="330df-115">이 함수는 올바른 파일 이름을 사용 하 여 [bcp_init](bcp-init.md) 를 호출한 후에만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="330df-115">This function can be called only after [bcp_init](bcp-init.md) has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="330df-116">기본값과는 다른 사용자 파일 형식을 사용하려는 경우에만 이 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="330df-116">You should call this function only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="330df-117">기본 사용자 파일 형식에 대 한 자세한 내용은 **bcp_init**를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="330df-117">For more information about a description of the default user-file format, see **bcp_init**.</span></span>  
  
 <span data-ttu-id="330df-118">를 호출한 후 `bcp_columns` 사용자 파일의 각 열에 대해 [bcp_colfmt](bcp-colfmt.md)를 호출 하 여 사용자 지정 파일 형식을 완전히 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="330df-118">After calling `bcp_columns`, you must call [bcp_colfmt](bcp-colfmt.md)for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330df-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="330df-119">See Also</span></span>  
 [<span data-ttu-id="330df-120">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="330df-120">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
