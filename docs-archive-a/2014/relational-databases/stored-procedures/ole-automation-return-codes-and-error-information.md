---
title: OLE 자동화 반환 코드 및 오류 정보 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- return codes [SQL Server]
- OLE Automation [SQL Server], return codes
- OLE Automation [SQL Server], errors
ms.assetid: 9696fb05-e9e8-4836-b359-d4de0be0eeb2
author: stevestein
ms.author: sstein
ms.openlocfilehash: aecdbaedca42b7456dbdbda0407760959e546f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661627"
---
# <a name="ole-automation-return-codes-and-error-information"></a><span data-ttu-id="2e712-102">OLE Automation 반환 코드 및 오류 정보</span><span class="sxs-lookup"><span data-stu-id="2e712-102">OLE Automation Return Codes and Error Information</span></span>
  <span data-ttu-id="2e712-103">OLE Automation 시스템 저장 프로시저는 기본 OLE Automation 작업에 의해 반환되는 HRESULT를 `int` 반환 코드로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-103">The OLE Automation system stored procedures return an `int` return code that is the HRESULT returned by the underlying OLE Automation operation.</span></span> <span data-ttu-id="2e712-104">HRESULT 값이 0이면 성공을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-104">An HRESULT of 0 indicates success.</span></span> <span data-ttu-id="2e712-105">0이 아닌 HRESULT는 0x800*nnnnn*16 진수 형태의 OLE 오류 코드이 고, `int` 저장 프로시저 반환 코드에서 값으로 반환 되는 경우 hresult의 형식은 214*nnnnnnn*입니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-105">A nonzero HRESULT is an OLE error code of the hexadecimal form 0x800*nnnnn*, but when returned as an `int` value in a stored procedure return code, HRESULT has the form 214*nnnnnnn*.</span></span>  
  
 <span data-ttu-id="2e712-106">예를 들어 잘못 된 개체 이름 (SQLDMO)을 전달 합니다. Sqldmo.xyzzy)로 sp_OACreate 하면 프로시저에서 `int` 2147221005의 HRESULT를 반환 합니다 .이 HRESULT는 16 진수의 0x800401f3입니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-106">For example, passing an invalid object name (SQLDMO.Xyzzy) to sp_OACreate causes the procedure to return an `int` HRESULT of 2147221005, which is 0x800401f3 in hexadecimal.</span></span>  
  
 <span data-ttu-id="2e712-107">`CONVERT(binary(4), @hresult)`를 사용하여 `int` HRESULT를 `binary` 값으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-107">You can use `CONVERT(binary(4), @hresult)` to convert an `int` HRESULT to a `binary` value.</span></span> <span data-ttu-id="2e712-108">그러나 `CONVERT(char(10), CONVERT(binary(4), @hresult))` 를 사용하면 HRESULT의 각 바이트가 하나의 ASCII 문자로 변환되어 알아볼 수 없는 문자열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-108">However, using `CONVERT(char(10), CONVERT(binary(4), @hresult))` results in an unreadable string, because each byte of the HRESULT is converted to a single ASCII character.</span></span> <span data-ttu-id="2e712-109">다음 샘플 HexToChar 저장 프로시저를 사용 하 여 HRESULT를 읽을 수 있는 `int` `char` 16 진수 문자열을 포함 하는 값으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-109">You can use the following sample HexToChar stored procedure to convert an `int` HRESULT to a `char` value that contains a readable hexadecimal string.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT name FROM sys.objects  
          WHERE name = N'dbo.sp_HexToChar')  
    DROP PROCEDURE HexToChar;  
GO  
CREATE PROCEDURE dbo.sp_HexToChar  
    @BinValue varbinary(255),  
    @HexCharValue nvarchar(255) OUTPUT  
AS  
    DECLARE @CharValue nvarchar(255);  
    DECLARE @Position int;  
    DECLARE @Length int;  
    DECLARE @HexString nchar(16);  
    SELECT @CharValue = N'0x';  
    SELECT @Position = 1;  
    SELECT @Length = DATALENGTH(@BinValue);  
    SELECT @HexString = N'0123456789ABCDEF';  
    WHILE (@Position <= @Length)  
    BEGIN  
        DECLARE @TempInt int;  
        DECLARE @FirstInt int;  
        DECLARE @SecondInt int;  
        SELECT @TempInt = CONVERT(int, SUBSTRING(@BinValue,@Position,1));  
        SELECT @FirstInt = FLOOR(@TempInt/16);  
        SELECT @SecondInt = @TempInt - (@FirstInt*16);  
        SELECT @CharValue = @CharValue +  
            SUBSTRING(@HexString, @FirstInt+1, 1) +  
            SUBSTRING(@HexString, @SecondInt+1, 1);  
        SELECT @Position = @Position + 1;  
    END  
    SELECT @HexCharValue = @CharValue;  
GO  
DECLARE @BinVariable varbinary(35);  
DECLARE @CharValue nvarchar(35);  
  
SET @BinVariable = 123456;  
  
EXECUTE dbo.sp_HexToChar  
    @binvalue = @BinVariable,  
    @HexCharValue = @CharValue OUTPUT;  
  
SELECT @BinVariable AS BinaryValue,  
    @CharValue AS CharacterRep;  
GO  
```  
  
 <span data-ttu-id="2e712-110">다음 예제 **sp_displayoaerrorinfo** 저장 프로시저를 사용하면 OLE Automation 프로시저 중 하나가 0이 아닌 HRESULT 반환 코드를 반환할 때 OLE Automation 오류 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-110">You can use the following sample stored procedure, **sp_displayoaerrorinfo** to display OLE Automation error information when one of the OLE Automation procedures returns a nonzero HRESULT return code.</span></span> <span data-ttu-id="2e712-111">이 예제 저장 프로시저는 `HexToChar` 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e712-111">This sample stored procedure uses `HexToChar`.</span></span>  
  
```  
CREATE PROCEDURE dbo.sp_DisplayOAErrorInfo  
    @Object int,  
    @HResult int  
AS  
    DECLARE @Output nvarchar(255);  
    DECLARE @HRHex nchar(10);  
    DECLARE @HR int;  
    DECLARE @Source nvarchar(255);  
    DECLARE @Description nvarchar(255);  
    PRINT N'OLE Automation Error Information';  
    EXEC HexToChar @HResult, @HRHex OUT;  
    SELECT @Output = N'  HRESULT: ' + @HRHex;  
    PRINT @Output;  
    EXEC @HR = sp_OAGetErrorInfo  
        @Object,  
        @Source OUT,  
        @Description OUT;  
    IF @HR = 0  
    BEGIN  
        SELECT @Output = N'  Source: ' + @Source;  
        PRINT @Output;  
        SELECT @Output = N'  Description: '  
               + @Description;  
        PRINT @Output;  
    END  
    ELSE  
    BEGIN  
       PRINT N' sp_OAGetErrorInfo failed.';  
       RETURN;  
    END  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="2e712-112">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2e712-112">Related Content</span></span>  
 [<span data-ttu-id="2e712-113">sp_OAGetErrorInfo&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e712-113">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
  
