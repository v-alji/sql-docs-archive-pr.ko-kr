---
title: 유니코드 데이터 및 서버 코드 페이지 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- Unicode [SQL Server], extended stored procedures
- extended stored procedures [SQL Server], metadata
ms.assetid: 52310260-a892-4b27-ad2e-bf164b98ee80
author: rothja
ms.author: jroth
ms.openlocfilehash: e88a43ee242e9fa84ac3a5573c7d3ca3dc0369d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638779"
---
# <a name="unicode-data-and-server-code-pages"></a><span data-ttu-id="e8f87-102">유니코드 데이터 및 서버 코드 페이지</span><span class="sxs-lookup"><span data-stu-id="e8f87-102">Unicode Data and Server Code Pages</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="e8f87-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8f87-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="e8f87-104">확장 저장 프로시저 API는 유니코드 데이터에 사용되지만 유니코드 메타데이터에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-104">The Extended Stored Procedure API is enabled for Unicode data; however, it is not enabled for Unicode metadata.</span></span> <span data-ttu-id="e8f87-105">#define 유니코드 지시문은 확장 저장 프로시저 API에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-105">The #define Unicode directive does not have any effect on the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="e8f87-106">확장 저장 프로시저 애플리케이션에 의해 반환되거나 확장 저장 프로시저 API에 제공되는 모든 메타데이터는 서버의 멀티바이트 코드 페이지에 있는 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-106">All metadata returned by, or provided to the Extended Stored Procedure API by your extended stored procedure application is assumed to be in the multibyte code page of the server.</span></span> <span data-ttu-id="e8f87-107">확장 저장 프로시저 API 서버 응용 프로그램의 기본 코드 페이지는 응용 프로그램이 실행 되는 컴퓨터의 ANSI 코드 페이지입니다 .이 페이지는 필드 매개 변수가 SRV_SPROC_CODEPAGE로 설정 된 **srv_pfield** 를 호출 하 여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-107">The default code page of an Extended Stored Procedure API server application is the ANSI code page of the computer on which the application is running, which can be obtained by calling **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE.</span></span>  
  
 <span data-ttu-id="e8f87-108">확장 저장 프로시저 API 애플리케이션에서 유니코드를 사용하는 경우 이 데이터를 확장 저장 프로시저 API로 전달하기 전에 유니코드 메타데이터 열 이름, 오류 메시지 등을 멀티바이트 데이터로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-108">If your Extended Stored Procedure API application is Unicode-enabled, you must convert your Unicode metadata column names, error messages, and so on, to multibyte data before passing this data to the Extended Stored Procedure API.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f87-109">예제</span><span class="sxs-lookup"><span data-stu-id="e8f87-109">Example</span></span>  
 <span data-ttu-id="e8f87-110">다음 확장 저장 프로시저는 설명된 유니코드 변환의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-110">The following extended stored procedure provides an example of the Unicode conversions discussed.</span></span> <span data-ttu-id="e8f87-111">다음 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f87-111">Note that:</span></span>  
  
-   <span data-ttu-id="e8f87-112">열이 SRVNVARCHAR에 설명 되어 있으므로 열 데이터는 **srv_describe** 에 유니코드 데이터로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-112">Column data is passed as Unicode data to **srv_describe** because the column is described to be SRVNVARCHAR.</span></span>  
  
-   <span data-ttu-id="e8f87-113">열 이름 메타 데이터는 멀티 바이트 데이터로 **srv_describe** 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-113">Column name metadata is passed to **srv_describe** as multibyte data.</span></span>  
  
     <span data-ttu-id="e8f87-114">확장 저장 프로시저는 필드 매개 변수가 SRV_SPROC_CODEPAGE로 설정 된 **srv_pfield** 를 호출 하 여의 멀티 바이트 코드 페이지를 가져옵니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e8f87-114">The extended stored procedure calls **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE to obtain the multibyte code page of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e8f87-115">오류 메시지는 멀티 바이트 데이터로 **srv_sendmsg** 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f87-115">Error messages are passed to **srv_sendmsg** as multibyte data.</span></span>  
  
    ```  
    __declspec(dllexport) RETCODE proc1 (SRV_PROC *srvproc)  
    {  
        #define MAX_COL_NAME_LEN 25  
        #define MAX_COL_DATA_LEN 50  
        #define MAX_ERR_MSG_LEN 250  
        #define MAX_SERVER_ERROR 20000  
        #define XP_ERROR_NUMBER MAX_SERVER_ERROR+1  
  
        int retval;  
        UINT serverCodePage;  
        CHAR *szServerCodePage;  
  
        WCHAR unicodeColumnName[MAX_COL_NAME_LEN];  
        CHAR multibyteColumnName[MAX_COL_NAME_LEN];  
  
        WCHAR unicodeColumnData[MAX_COL_DATA_LEN];  
  
        WCHAR unicodeErrorMessage[MAX_ERR_MSG_LEN];  
        CHAR  multibyteErrorMessage[MAX_ERR_MSG_LEN];  
  
        lstrcpyW (unicodeColumnName, L"column1");  
        lstrcpyW (unicodeColumnData, L"column1 data");  
        lstrcpyW (unicodeErrorMessage, L"No Error!");  
  
        // Obtain server code page.  
        //  
        szServerCodePage = srv_pfield (srvproc, SRV_SPROC_CODEPAGE, NULL);      
        if (NULL != szServerCodePage)  
            serverCodePage = atol(szServerCodePage);  
        else   
        {   // Problem situation exists.  
            srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
            return 1;  
        }  
  
        // Convert column name for Unicode to multibyte using the   
        // server code page.  
        //  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeColumnName,              // wide-character string  
            -1,                             // string is null terminated  
            multibyteColumnName,            // address of buffer for new  
                                            //   string  
            sizeof (multibyteColumnName),   // size of buffer  
            NULL, NULL);  
  
        if (0 == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"Conversion to multibyte  
            failed.");  
            goto Error;  
        }  
  
        retval = srv_describe (srvproc, 1, multibyteColumnName,  
        SRV_NULLTERM,   
          SRVNVARCHAR, MAX_COL_DATA_LEN*sizeof(WCHAR), // destination  
            SRVNVARCHAR, lstrlenW(unicodeColumnData)*sizeof(WCHAR),  
            unicodeColumnData); //source  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_describe failed.");  
            goto Error;  
        }  
  
       retval = srv_sendrow(srvproc);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_sendrow failed.");  
            goto Error;  
        }  
  
        retval = srv_senddone (srvproc, SRV_DONE_MORE|SRV_DONE_COUNT, 0, 1);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_senddone failed.");  
            goto Error;  
        }  
  
        return 0;  
    Error:  
        // convert error message from Unicode to multibyte.  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeErrorMessage,            // wide-character string  
            -1,                             // string is null terminated  
            multibyteErrorMessage,          // address of buffer for new  
                                            //   string  
            sizeof (multibyteErrorMessage), // size of buffer  
            NULL, NULL);  
  
    srv_sendmsg(srvproc, SRV_MSG_ERROR, XP_ERROR_NUMBER, SRV_INFO, 1,  
                NULL, 0, __LINE__,   
                multibyteErrorMessage,  
                SRV_NULLTERM);  
  
        srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
  
        return 1;  
    }  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8f87-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8f87-116">See Also</span></span>  
 [<span data-ttu-id="e8f87-117">srv_wsendmsg &#40;확장 저장 프로시저 API&#41;</span><span class="sxs-lookup"><span data-stu-id="e8f87-117">srv_wsendmsg &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)  
  
  
